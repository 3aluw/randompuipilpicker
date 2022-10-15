<template>
<div class="container">
  <p><strong>Seperate names Using a comma "," or write every name on a new line</strong></p>
<input type="text" v-model="newList.listName"  placeholder="insert list name" maxlength="18"> <br>
<textarea placeholder="insert names seperated" class="names-input" type="text"  v-model="newList.names" ></textarea>
 <button @click="listCreatorEmitter"> Create a new List </button>
 <p v-if="error" class="error-message"><strong>ERROR! :</strong> enter a name for your list, and your student's names</p>
 </div>
</template>


<script>



export default {
  name: 'Home',
   emits: ["new-list"],

  data(){
    return{
      error: false,
      newList:{
        listName: null,
        names: null,
        unusedNames: null,
      }
    }
  },

methods:{
  listCreatorEmitter(e){ 
    
  if( !Boolean(this.newList.names)|| !Boolean(this.newList.listName)){
   this.error = true;
  setTimeout(()=>this.error =false ,5000)
   
  }else{
     this.newList.names = this.newList.names.trim().split(/\s*[,\n]\s*/);
    
      this.newList.unusedNames = [...this.newList.names];
      let newListCopy = JSON.parse(JSON.stringify(this.newList))
      console.log(newListCopy)
    this.$emit("new-list", newListCopy);
  this.newList.names = this.newList.listName = "";
  
  
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
.error-message{
  position: absolute;
  bottom: 0;
  left: 0;
  background-color: rgb(155, 77, 77);
  color: white;
  padding: 1rem;
  padding-inline: 2rem;
}
.error-message strong{
  color: rgb(238, 211, 211);
  font-weight: 900;
}
  </style>