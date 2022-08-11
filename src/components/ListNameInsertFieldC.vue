<template>
 <div class="container"> 
<input type="text" v-model="NewlistName" @input="arrayCreator" placeholder="insert list name" > <br>
<button @click="arrayCreator"> Create a new array </button>
 </div>
</template>

<script>
export default {
  name: 'ListNameInsertFieldC',
data(){
  return{
NewlistName : "",

  }
},
methods:{
  arrayCreator(){
    this.$emit("NewListName", this.NewlistName);
  },
}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
