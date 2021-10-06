<template>
  <div>
    <Loader v-if="showloading">
      <template>
        <span>Loading.....</span>
      </template>
    </Loader>
    <div v-else>
      <div class="searchBar">
        <input v-model="search" type="text" placeholder="search" />
      </div>
      <div class="postMain">
        <div class="postList" v-for="data in postsList" :key="data.id">
          <h3 class="postListTitle">{{ data.id }}</h3>
          <p class="postListBody">{{ data.body }}</p>
          <div class="postListButton">
            <button @click="deleteConfirm()">Delete</button>
            <Alert v-if="showAlert" class="alert">
              <img style="height: 120px;" src="/images/rightTick.jpeg" alt="Rightlogo" />
              <h4>Are You Sure?</h4>
              <p style="font-size: 18px">Do you really want to delete these records? This process cannot be undone</p>
              <button @click="cancelDelete()" id="cancelButton">Cancel</button>
              <button @click="DeleteItem(data.id)">Delete</button>
            </Alert>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import axios from "axios";
import Loader from "./Loader.vue";
import Alert from "./Alert.vue";
export default {
  name: "Project2",
  components: {
    Loader,
    Alert,
  },
  data() {
    return {
      posts: null,
      search: "",
      showloading: true,
      showAlert: false,
    };
  },
  methods: {
    DeleteItem(itemtodelete) {
      this.posts = this.posts.filter((data) => {
        return data.id != itemtodelete;
      });
      this.showAlert = false;
      console.log(this.posts);
    },
    cancelDelete() {
      this.showAlert = false;
    },
    deleteConfirm() {
      this.showAlert = true;
    },
  },
  created() {
    axios
      .get("https://jsonplaceholder.typicode.com/posts")
      .then((response) => {
        this.posts = response.data;
        console.log(response);
        this.showloading = false;
      })
      .catch(() => {
        console.log("error");
      });
  },
  computed: {
    postsList() {
      return this.posts.filter((data) => data.body.includes(this.search)).slice(0, 10);
    },
  },
};
</script>
<style scoped>
.postList {
  border: 1px solid rgb(233, 230, 230);
  box-shadow: 1px 1px 5px 5px rgb(233, 230, 230);
  border-radius: 4px;
  /* height: 350px; */
  width: 390px;
  margin: 25px;
  margin-left: 50px;
  background-color: #ffff;
}
.postMain {
  display: flex;
  flex-wrap: wrap;
}
.postListButton {
  display: flex;
  justify-content: space-around;
  border-top: 2px solid rgb(241, 238, 238);
  margin-top: -10px;
}
.postListButton button {
  margin: 20px;
  height: 45px;
  width: 100px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  font-size: 20px;
  font-weight: 600;
  color: white;
  background-color: #78e4b9;
  transition: all 1s ease-in-out 0.1s;
}
.postListButton button:hover {
  box-shadow: 1px 1px 5px 5px #93c5fd;
  background-color: #78e4b9;
  /* transform: rotate(90deg); */
  /* transform:skew(50deg) ; */
  /* transform: scale(0.5); */
  /* transform: translateX(123px); */
  /* transform: translatey(50px); */
  /* transform: translate(123px,123px); */
}
.postListTitle {
  border-bottom: 2px solid rgb(241, 238, 238);
  padding: 10px;
}
.postListBody {
  height: 220px;
  padding: 10px;
  padding-bottom: 10px;
  margin-top: -20px;
}
.searchBar input {
  height: 40px;
  width: 55%;
  outline: none;
  border: 2px solid rgb(224, 219, 219);
  border-radius: 5px;
  padding-left: 20px;
}
.searchBar input:hover {
  box-shadow: 1px 1px 3px 3px rgb(224, 219, 219);
  border-radius: 7px;
}
.searchBar {
  text-align: left;
  margin-left: 55px;
  margin-top: 20px;
  margin-bottom: 10px;
}
.header {
  border-bottom: 2px solid rgb(238, 233, 233);
  height: 100px;
}
.alert button {
  height: 40px;
  width: 80px;
  margin: 10px;
  border: none;
  border-radius: 5px;
  background-color: rgb(192, 84, 84);
  color: #fff;
  font-size: 17px;
  transition: none;
}
.alert button:hover{
    box-shadow: 1px 1px 2px 1px red;
    background-color: red;
}
#cancelButton {
  background-color: rgb(165, 162, 162);
}
#cancelButton:hover{
    box-shadow: 1px 1px 2px 1px grey;
    background-color: gray;
}
/* .alert{ */
    /* transition: all 10s ease-in-out 2s; */

/* } */
</style>