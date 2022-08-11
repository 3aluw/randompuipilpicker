<template>
<div class="container">
<input type="text" v-model="newList.listName"  placeholder="insert list name" > <br>
<textarea class="names-input" type="text"  v-model="newList.names" ></textarea>
 <button @click="listCreatorEmitter"> Create a new array </button>
 <p v-if="error">please enter a name for your list, and your student's names</p>
 </div>
</template>


<script>



export default {
  name: 'Home',
   emits: ["inserted-names-array"],

  data(){
    return{
      error: false,
      newList:{
        listName: null,
        names: null,
        arr:[]
      }
    }
  },

methods:{
  listCreatorEmitter(e){
  if(this.newList.names==false || this.newList.listName == false){
   this.error = true
  }else{
     this.newList.names = this.newList.names.trim().split(/\s*,\s*/);
    console.log( this.newList)
  }
  },

}}

  </Script> 
  <style scoped>
textarea{
     display: block;
    margin: 0 auto;
    margin-block: 1rem;
}
.names-input{
  margin-block: 1rem;
  box-sizing: border-box;
border: 0.5px black solid;
border-radius: 3px;
min-height: 40vh;
min-width: 50vw;
text-align: left;
padding: 0.8rem;
  }

  </style>