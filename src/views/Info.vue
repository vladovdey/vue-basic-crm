<template>
  <div class="home">
    <div class="menu">
      <div class="burger-icon__container"></div>
      Coodo
    </div>
    <div class="basic-table">
      <div v-for="user in users" :key="user.id" class="basic-table__row">
        <div class="basic-table_column">
          {{ user.id }}
        </div>
        <div class="basic-table_column">
          {{ user.userName }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
// import HelloWorld from "@/components/HelloWorld.vue";

export default {
  name: "Home",
  components: {
    // HelloWorld,
  },
  data: () => {
    return {
      users: Array,
    };
  },
  methods: {

  },
  created: function () {
    // async fetch("http://localhost:3000/user")
    //   // .then((response) => {
    //   //   console.log(response);
    //   //   this.users = JSON.parse(response);
    //   //   console.log(this.users);
    //   // })
    //   .then((response) => {
    //     return response.json();
    //   })
    //   .then((data) => {
    //     this.users = data;
    //   });
    fetch("http://localhost:3000/user")
    .then((response)=>{
      return response.json();
    })
    .then((data)=>{
      console.log(data);
      this.users = data;
    })

    // async ()=>{
    //   let response = await fetch("http://localhost:3000/user");
    //   this.users = await response.json();
    // }
    console.log(this.users);
  }
};
</script>
