<template>
  <div id="app">



    <div class="container">
    <!-- trigger button the create new post modal -->
    <button type="button" class="btn btn-primary m-2 fload-end" data-toggle="modal" data-target="#exampleModal">
      Add our own Post
    </button>
    <!--end trigger button the create new post modal -->

    <button type="button" class="btn btn-secondary m-2 fload-end" v-on:click="PostJsonApi()">Add a post from API</button>

      <div class="card-deck">
        <div class="col-sm-6 col-md-4 col-lg-3" v-for="todo of todos" v-bind:key="todo.id">
          <div class="card mb-5">
            <div class="card-body">
              <p>ID: {{ todo.id }}</p>
              <h5 class="card-title">{{ todo.title }}</h5>
              <p class="card-text">{{ todo.body }}</p>
              <button type="button" class="btn btn-light mr-1" data-toggle="modal" data-target="#exampleModal{todo.id}"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-pencil-square" viewBox="0 0 16 16">
              <path d="M15.502 1.94a.5.5 0 0 1 0 .706L14.459 3.69l-2-2L13.502.646a.5.5 0 0 1 .707 0l1.293 1.293zm-1.75 2.456-2-2L4.939 9.21a.5.5 0 0 0-.121.196l-.805 2.414a.25.25 0 0 0 .316.316l2.414-.805a.5.5 0 0 0 .196-.12l6.813-6.814z"/>
              <path fill-rule="evenodd" d="M1 13.5A1.5 1.5 0 0 0 2.5 15h11a1.5 1.5 0 0 0 1.5-1.5v-6a.5.5 0 0 0-1 0v6a.5.5 0 0 1-.5.5h-11a.5.5 0 0 1-.5-.5v-11a.5.5 0 0 1 .5-.5H9a.5.5 0 0 0 0-1H2.5A1.5 1.5 0 0 0 1 2.5v11z"/>
              </svg></button>
              <button type="button" class="btn btn-light mr-1" v-on:click="DeleteApi(todo.id)"><svg xmlns="http://www.w3.org/2000/svg" width="16" height="16" fill="currentColor" class="bi bi-trash" viewBox="0 0 16 16">
              <path d="M5.5 5.5A.5.5 0 0 1 6 6v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm2.5 0a.5.5 0 0 1 .5.5v6a.5.5 0 0 1-1 0V6a.5.5 0 0 1 .5-.5zm3 .5a.5.5 0 0 0-1 0v6a.5.5 0 0 0 1 0V6z"/>
              <path fill-rule="evenodd" d="M14.5 3a1 1 0 0 1-1 1H13v9a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2V4h-.5a1 1 0 0 1-1-1V2a1 1 0 0 1 1-1H6a1 1 0 0 1 1-1h2a1 1 0 0 1 1 1h3.5a1 1 0 0 1 1 1v1zM4.118 4 4 4.059V13a1 1 0 0 0 1 1h6a1 1 0 0 0 1-1V4.059L11.882 4H4.118zM2.5 3V2h11v1h-11z"/>
              </svg></button>
            </div>
          </div>
        </div>
      </div>
    </div>

    <!--Create new post Modal-->
    <div class="modal fade" id="exampleModal" tabindex="-1" aria-labelledby="exampleModalLabel" aria-hidden="true">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Create your own post</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
          <div class="input-group mb-3">
              <span class="input-group-text mr-2">post title:</span>
              <input class="w-75" type="text" v-model="nameis" v-on:keyup.enter="PostApi()" />
              <span class="input-group-text mr-2 mt-4">post text:</span>
              <input class="w-75 mt-4" type="text" v-model="bodyis" v-on:keyup.enter="PostApi()" />
              <button class="btn btn-success mt-4" v-on:click="PostApi()">Create a post</button>
          </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
          </div>
        </div>
      </div>
    </div>
    <!-- End of the create new post Modal -->



    <!--show post Modal-->
    <div v-for="todo of todos" v-bind:key="todo.id">
    <div class="modal fade" id="exampleModal{todo.id}" tabindex="-1" aria-labelledby="exampleModalLabel{todo.id}" aria-hidden="true" >
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">Create your own post</h5>
            <button type="button" class="close" data-dismiss="modal" aria-label="Close">
              <span aria-hidden="true">&times;</span>
            </button>
          </div>
          <div class="modal-body">
          <div class="input-group mb-3">
              <span class="input-group-text mr-2">post title:</span>
              <input class="w-75" type="text" v-model="nameis" v-on:keyup.enter="PostApi()" />
              <span class="input-group-text mr-2 mt-4">post text:</span>
              <input class="w-75 mt-4" type="text" v-model="bodyis" v-on:keyup.enter="PostApi()" />
              <button class="btn btn-success mt-4" v-on:click="PostApi()">Create a post</button>
          </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-secondary" data-dismiss="modal">Close</button>
          </div>
        </div>
      </div>
    </div>
    </div>
    <!-- End of the create new post Modal -->

</div>
</template>

<script>
import axios from "axios";
const baseUrl = "http://localhost:3000/todos/";
const apiUrl = "https://jsonplaceholder.typicode.com/";
console.log(apiUrl);
export default {
  name: 'App',
  data() {
    return{
      todos:[],
      nameis:'',
      bodyis:'',
    }
  },
  methods: {
    async GetApiUrl(){
      await axios.get(baseUrl).then((resp) => {this.todos = resp.data}).catch((err) => {console.log(err);});
    },
    async GetApi(){
      await axios.get(baseUrl).then((resp) => {this.todos = resp.data}).catch((err) => {console.log(err);});
    },
    async PostApi(){
      await axios.post(baseUrl, {title:this.nameis,body:this.bodyis}).then((resp) => {console.log(resp); this.nameis=''; this.bodyis=''; this.GetApi(); }).catch((err) => {console.log(err);});
    },
    async DeleteApi(id){
      await axios.delete(baseUrl+id).then((resp) => {console.log(resp); this.GetApi(); }).catch((err) => {console.log(err);});
    },
    async UpdateApi(id,title){
      await axios.put(baseUrl+id, {title:title}).then((resp) => {console.log(resp); this.GetApi(); }).catch((err) => {console.log(err);});
    },
    async PostJsonApi(){
      //todo get a fake post from https://jsonplaceholder.typicode.com/posts/1
    },
  },
  mounted(){
    this.GetApi();
  }
};
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
