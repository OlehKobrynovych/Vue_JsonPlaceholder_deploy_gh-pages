<template>
  <div class="labelWrap">
      <div class="wrapp">
          <h3>Post editing</h3>
            <label class="labelEdit">
                <div>Post name</div>
                <input v-model="editName" placeholder="Post name" />
            </label>
            <label class="labelEdit">
                <div>Post body</div>
                <textarea v-model="editBody" placeholder="Post body" rows="5" cols="20"></textarea>
            </label>
            <label class="labelEdit">
                <div>Email</div>
                <input type="email" v-model="editEmail" placeholder="Email" />
            </label>
            <button @click="heandelEditPost(editName, editBody, editEmail)" :disabled="!editName.length || !editBody.length || !editEmail.length">Send</button>
            <div @click="heandeClose()" class="closeBtn">X</div>
        </div>
  </div>
</template>

<script>
export default {
  //  components: { EditPost, EditPost1 }
    // components: {       
    //   // EditPost
    
    // },
     props: {
         heandelEditPost: {
            type: Function,
            default: () => {},
        },
         heandeClose: {
            type: Function,
            default: () => {},
        },
    },
    data() {
        return {
           editName: '',
           editBody: '',
           editEmail: ''
        };
    },
    mounted() {
    },
    //  watch: {        
    //     // 1. 
    //     editName: {
    //         handler(newAsdasd, prevAsdasd) {
    //             if (newAsdasd && prevAsdasd) {
    //                 this.asd = 12;
    //             }
    //         },
    //         deep: true,                    
    //     },
    //  },
    methods: {
       
    },
 
}
</script>

<style scoped>
.labelWrap {
    position: fixed;
    width: 800px;
    background-color: #d0b4b4;
    left: 50%;
    transform: translate(-50%, 0);
}
.labelEdit {
    display: block;
    align-items: center;
    justify-content: center;
    margin: 7px;
}
.closeBtn {
    position: absolute;
    display: inline-block;
    top: 4px;
    right: 19px;
    cursor: pointer;
    color: red;
    padding: 6px;
    border: 1px solid;
    border-radius: 34%;
}
.wrapp {
    position: relative;
}
</style>