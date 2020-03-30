<template>
  <div id="container">
    <h2 id="safe">#StaySafe</h2>
    <h1 class="logo">Api User Form</h1>
    <h6>By Godwin</h6>
    <div class="row mt-1">
      <div class="col-md-12 offset-md-2">
        <form id="form-box">
          <div class="input-group mb-2">
            <input
              v-model="name"
              type="text"
              placeholder="Enter Username"
              class="form-control"
            />
            <div class="input-group-append">
              <button type="button" @click="addUser" class="btn btn-warning">
                Add User
              </button>
            </div>
          </div>
        </form>
      </div>
      <div class="col-md-12">
        <ul class="list-group">
          <li class="list-group-item" v-for="user in users" :key="user.id">
            {{ user.name }} <br>
            <small>{{user.phone}} {{user.email}}</small>
            <div class="span" @click="del(user)">
              <span @click="del(user)">X</span>
            </div>
          </li>
        </ul>
      </div>
    </div>
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Profile",
  components: {
    // Profile
  },
  data() {
    return {
      users: [],
      name: null
    };
  },
  async created() {
    let getUsers = await axios.get(
      "https://jsonplaceholder.typicode.com/users"
    );
    this.users = getUsers.data;
  },
  methods: {
        checkDuplicate(newUserName) {
      this.users.forEach(user => {
        if (user.name === newUserName || user.newUserName.value === "") {
          alert("This task already exists");
          this.newUserName = null;
          this.users.push({name: this.newuser});

        }
      });
      
    },
      addUser() {
      if (!this.checkDuplicate(this.name)) {
        let lastUserIndex = this.users.length - 1;
        let lastUser = this.users[lastUserIndex];
        let newUserId = lastUser.id + 1;
        let newUser = {
          id: newUserId,
          name: this.name
        };
        this.users.push(newUser);
        this.name = "";
      }
    },
    
    
    del(user) {
      this.users = this.users.filter(delUser=> delUser.id !== user.id);
      console.log(user.id);
    }
  }
};
</script>

<style scoped>
   @import url("https://fonts.googleapis.com/css?family=Pacifico|Roboto");
h1.logo {
  color: #000;
  font-family: 'Pacifico', cursive;
  font-size: 4em;
  margin-bottom:0.2em;}
#container {
  height: 100vh;
  display: flex;
  flex-direction: column;
  justify-content: top;
  align-items: center; }

#form-box {
  background: #fff;
  position: relative;
  width: 600px;
  border-top-right-radius: 5px;
  border-top-left-radius: 5px;
  box-shadow: white 2px 2px 20px;
  /* box-shadow: 0 16px 24px 2px rgba(0, 0, 0, 0.1), 0 6px 10px 5px rgba(0, 0, 0, 0.1), 0 8px 10px -5px rgba(0, 0, 0, 0.2); */
  transition: transform 0.1s ease-in-out; }

  span {
  color: red;
  float: right;
  cursor: pointer;
  width: 20px;
  float: right;
}
span:hover{
  color:white
}
.span:hover{
    background-color: red;
    color: white;
    padding: 1vmin;
    font-size: 10px;
    border-radius: 50%;
    float: right;
    cursor: pointer;
}
#safe {
  height: 40px;
  width: 150px;
  text-align: center;
  padding: 0 auto;
  margin: 0 auto;
  background-color: red;
  animation-name: stretch;
  animation-duration: 1.5s; 
  animation-timing-function: cubic-bezier(0.1, 0.7, 1.0, 0.1); 
  animation-delay: 0;
  animation-direction: alternate;
  animation-iteration-count: infinite;
  animation-fill-mode: none;
  animation-play-state: running;
}

@keyframes stretch {
  0% {
    transform: scale(.3);
    background-color: red;
    border-radius: 100%;
  }
  50% {
    background-color: orange;
  }
  100% {
    transform: scale(1.5);
    background-color: yellow;
  }
}

</style>