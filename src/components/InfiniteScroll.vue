<style>

.scroll-wrap {
  width: 60%;
  margin-left: 20%;
  max-height: 40vh;
  overflow: auto;
  margin-top: 50px;
  padding: 25px;
}

.scroll-wrap .card {
  box-shadow: 0 4px 8px 0 rgba(0,0,0,0.2);
  transition: 0.3s;
  border-radius: 5px;
  margin-top:20px; 
}

.scroll-wrap .card:hover {
  box-shadow: 0 8px 16px 0 rgba(0,0,0,0.2);
}

.scroll-wrap img {
  border-radius: 5px 5px 0 0;
}

.scroll-wrap .container {
  padding: 2px 16px;
}

</style>

<template>
  <div class="scroll-wrap" v-on:scroll.passive="handleScroll">
    <div v-for="item in users" :key="item.login.uuid">
      <div class="card">
      <img :src="item.picture.thumbnail" alt="Avatar"/>
      <div class="container">
        <h4>{{item.name.title}}. {{item.name.first}} {{item.name.last}}</h4>
        <p><b>Email:</b>{{item.email}}</p>
        <p><b>Phone:</b>{{item.cell}}</p>
        <p><b>Age:</b>{{item.dob.age}}</p>
        <p><b>Gender:</b>{{item.gender}}</p>
        <p><b>Nationality:</b>{{item.nat}}</p>        
        <p><b>Address:</b>{{item.location.country}},{{item.location.state}},{{item.location.city}},{{item.location.street.name}}-{{item.location.street.number}}</p>
        <p><b>Postcode:</b>{{item.location.postcode}}</p>
        <p><b>Timezone:</b>{{item.location.timezone.offset}}({{item.location.timezone.description}})</p>
        <p><b>Location:</b> <a :href="'https://www.google.com/maps?q='+item.location.coordinates.latitude+','+item.location.coordinates.longitude" target="_blank">{{item.location.coordinates.latitude}},{{item.location.coordinates.longitude}}</a></p>
      </div>
    </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";

export default {
  name: "InfiniteScroll",
  data: () => {
    return {
      users: []
    };
  },
  methods: {
    loadListing() {
      for (var i = 0; i <5; i++) {
        this.loadMore();
      }
    },
    loadMore() {
      axios.get(`https://randomuser.me/api/`).then(response => {

        this.users.push(response.data.results[0]);
      });
    },
    handleScroll() {
      this.loadMore();
    }
  },
  created() {
    window.addEventListener("scroll", this.handleScroll);
  },
  destroyed() {
    window.removeEventListener("scroll", this.handleScroll);
  },
  beforeMount() {
    this.loadListing();
  }
};
</script>
