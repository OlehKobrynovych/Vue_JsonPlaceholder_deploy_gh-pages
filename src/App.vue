<template>
    <div id="app">
        <img src="./assets/logo.png">
        <HelloWorld/>
        <Search :onUserSearch="onUserSearch" />

        <div class="commentsCartWrap">
            <EditPost v-if="edit" :heandelEditPost="heandelEditPost" :heandeClose="heandeClose" />
            <!-- <div class="commentsCart" v-for='el of comments' :key='el.id'> -->
            <div class="commentsCart" v-for='el of commentsFilterUser' :key='el.id'>
                <div>Post User {{el.postId}}</div>
                <div><h2>{{el.name}}</h2></div>
                <div>{{el.body}}</div>
                <div><a href="#">{{el.email}}</a></div>
                <button v-on:click="onEditPost(el.id)" class="editBtn">Edit</button>
            </div>
        </div>
        
    </div>
</template>

<script>
import HelloWorld from './components/HelloWorld';
import Search from "./components/Search.vue";
import EditPost from "./components/EditPost.vue";

export default {
    name: 'App',

    components: {
        HelloWorld,
        Search,
        EditPost,
    },

    props: {
    },

    data() {
        return {
            comments: [],
            edit: false,
            editPostName: '',
            editPostBody: '',
            editPostEmail: '',
            editPostId: null,
            userSearch: 1,
        };
    },

    mounted() {
        this.getDate();
    },

    watch: {    
      // userSearch: {
      //     handler(newAsdasd, prevAsdasd) {
      //         if (newAsdasd && prevAsdasd) {
      //             this.asd = 12;
      //         }
      //     },
      // },
    },

    computed: {           
        commentsFilterUser() {   
          // this.userSearch   
          // debugger
          return this.userSearch ? this.comments.filter(el => el.postId === Number(this.userSearch)) : this.comments ;
        },
    },

    methods: {
        getDate() {
            fetch("https://jsonplaceholder.typicode.com/comments")
                .then(response => response.json())
                .then(json => {
                this.comments = json;
            });
        },

        onEditPost(id) {
            this.edit = true;
            this.editPostId = id;
        },
        
        heandeClose() {
            this.edit = false;
        },
        
        onUserSearch(value) {
            this.userSearch = value;
        },

        heandelEditPost(editName, editBody, editEmail) {
          this.edit = false;
          this.comments=this.comments.map(el => {
            if (el.id == this.editPostId) {
                el.name = editName
                el.body = editBody
                el.email = editEmail
            }
            return el
          })
        }
    },
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

.commentsCartWrap {
  /* position: relative; */
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
  
}
.commentsCart {
  border: 2px solid rgb(12, 157, 214);
  width: 48.333333%;
  padding: 4px;
  margin: 4px;
}
.editBtn {
    background-color: cadetblue;
    display: inline-block;
    width: 100px;
    padding: 10px;
    margin: 10px;
    cursor: pointer;
    border-radius: 15px;
}
</style>
