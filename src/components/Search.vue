<template>
  <div class="labelWrap">
    <label class="labelEdit">
        <div>Search User</div>
        <input type="number" v-model="searchValue" placeholder="Enter the User number" />
    </label>
  </div>
</template>

<script>


export default {

  //  components: { EditPost, EditPost1 }
    // components: {       
    //   // EditPost
    
    // },

     props: {
        onUserSearch: {
            type: Function
        },
    },

    data() {
        return {
            searchValue: 1
         
          
        };
    },
    mounted() {
    },

    watch: {    
      searchValue: {
          handler(newValue, prevValue) {
              this.onUserSearch(newValue)
          },
      },
    },

    methods: {
       
    },
 
}

</script>

<style scoped>




</style>
