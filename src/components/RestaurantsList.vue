<template>
  <div class="container">
    <h1 class="font-italic">{{ msg }}</h1>
    <table class="mt-5">
      <tr v-for="restaurants in restaurantsList" :key="restaurants.id">
        <td v-for="restaurant in restaurants" 
          :key="restaurant.id"
          :class="{ hide: restaurant.address.city === 'Bielefeld'}">
          <h2 class="font-italic">{{restaurant.name}}</h2>
          <h4 v-if="restaurant.desc.length > 20">{{restaurant.desc.substring(0,20)+"..."}}</h4>
          <h4 v-else>{{restaurant.desc}}</h4>
          <button type="button" class="btn btn-secondary mt-3" data-toggle="collapse" :data-target="'#restaurant'+restaurant.id">Contact information</button>
          <div :id="'restaurant'+restaurant.id" class="collapse">
            <p class="mt-3">Tel: {{restaurant.phone}}</br>
              Address: {{restaurant.address.number}} 
              {{restaurant.address.street}}
              {{restaurant.address.city}},
              {{restaurant.address.country}}
            </p>
          </div>
        </td>
      </tr>
    </table>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "RestaurantsList",
  props: {
    msg: String
  },
  data() {
    return {
      restaurantsList: []
    };
  },
  created() {
    axios
      .get("https://waraclecodetesting.azurewebsites.net/api/restaurants")
      .then(response => {
        this.restaurantsList = response.data;
      })
      .catch(error => {
        console.log("There was an error" + error.response);
      });
  }
};
</script>

<style scoped>
table {
  width: 100%;
}
td {
  width: 100%;
  display: block;
  padding: 20px;
  margin-bottom: 20px;
  border: 2px solid #cbb676;
}
h4 {
  color: #ce6e11;
}
.hide {
  display: none;
}
</style>