<template>

  <div class="lists-container">
<div class="saved-list" v-for="(list, index) in lists" :key="list.listName" @click="listExtrcat(index)"> 
 {{list.listName}}
</div></div>
<button @click="studentSelector">Pick someone</button>
<button @click="saver">Save List</button>
<h1>{{pickedP}}</h1>
<h2>reamaining students : {{currentObj.unusedNames.length}}</h2>

</template>

<script>


export default {
  name: 'Home',
  props:{
    newObj: Object,
  },
   emits: ["new-list"],

  data(){
    return{
     pickedP: null,
      currentObj:{
      listName:null,
      names:null,
      unusedNames: null,
    },
      currentObjIndex : 0,
    lists:[{
      listName:"demo",
      names:["Alexcia","Daja","Shakira","Eleanor","Josefina","Kalli","Adrian","Nallely","Deondre","Elian","Aliya","Britney","Ricky","Annika","Kinsley","Sidney","Oliver","Quinn","Raymond","Jerimiah","Maya","Nathan","Antonio","Simone","Amira","Tara","Gerald","Devon","Brynn","Ruth"],
       unusedNames: ["Shakira","Eleanor","Josefina","Kalli","Adrian","Nallely",]
    },
 
    
    ],
    
    }
  },

   beforeMount() {
   if(this.currentObj.listName === null){ this.currentObj = this.lists[0]}; 
   if(Object.keys(this.newObj).length !== 0) {this.lists.push(this.newObj);
   }
  }, 
  activated(){
    console.log(1,this.lists)
  },
  deactivated(){
    console.log(2,this.lists)
  },
  
  methods:{
    listExtrcat(index){
this.currentObj.listName = this.lists[index].listName;
this.currentObj.unusedNames = this.lists[index].unusedNames;
this.currentObjIndex = index;

},
 studentSelector(){



  let pickedN = Math.floor(Math.random()*this.currentObj.unusedNames.length);
  this.pickedP = this.currentObj.unusedNames[pickedN]
  this.currentObj.unusedNames.splice(pickedN,1);

    if( this.currentObj.unusedNames.length === 0){
      this.currentObj.unusedNames = [...this.currentObj.names];
     
      
    }

},
saver(){
  this.lists.splice(this.currentObjIndex ,1,this.currentObj);
  
}
}

}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
h1{
      height: 2rem;
}
button{
  background: #B39CD0;
  border: 2px solid #B39CD0;
  color: black;
  font-size: 1rem;
  font-family: 'Lucida Sans', 'Lucida Sans Regular', 'Lucida Grande', 'Lucida Sans Unicode', Geneva, Verdana, sans-serif;
  border-radius: 3px;
  margin: 1rem;
  padding: .5rem;
  cursor: pointer;
  min-width: 10vw;
  min-height: 3vh;
}
button:hover{
  background: none;
  color: black;
}
input{
  min-width: 50vw;
  min-height: 10vh;
  font-size: 3rem;
  text-align: center;
}
.lists-container{
  display: flex;
  flex-direction: row;
}

.saved-list{
  margin: 0.5rem;
 min-height: 8rem;
 min-width:10rem ;
  border: 1px solid black;
  padding: 10px;
    display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;  
  color: #845EC2;
  font-size: 3rem;
}
</style>
