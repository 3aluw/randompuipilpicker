<template>

  <div class="lists-container">
<div class="saved-list" v-for="(list, index) in lists" :key="list.number" @click="listExtrcat(index)"> 
 {{list.number}}
</div></div>
<button @click="studentSelector">Pick someone</button>
<button @click="saver">Save List</button>
<h1>{{pickedP}}</h1>
<h2>reamaining students : {{currentObj.arr.length}}</h2>
</template>

<script>


export default {
  name: 'Home',
   emits: ["inserted-names-array"],

  data(){
    return{
        arr:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10, 11, 12, 13, 14, 15, 16, 17, 18, 19, 20, 21, 22, 23, 24, 25, 26, 27, 28, 29, 30],
    
      names:["تجرونة بشرى ","باباوموسى هدى","التومي مارية","بوحديبه غنية","موسى وعلي باية","بابنات مروة","شقبقب فاطمة الزهراء","أويابة سارة","قزريط أسماء","بوسنان سعاد","بوكرموش حفصة","الشيخ صالح فطيمة بنت","حمدي بابا مريم","بوكرموش سيرين","حجاج إسراء","امسيرد ضحى","ليسير بشرى","البدري رحمة","ارفيس فردوس","الشيخ صالح مارية","عوف نسيمة بنت","بازين سلسبيل","بوحديبه خديجة","اويابه بشرى","بابنات صفاء","عطفاوي مامه بنت","باباواسماعيل ملاك","طباخ زينب","قزريط إكرام","موسى وعلي زينب","أوزايد مامة لالة"]
     ,
     pickedP: null,
      currentObj:{
      number:null,
      arr: null
    },
      currentObjIndex : 0,
    lists:[{
      number:"demo",
      arr: [0,1,2,3,4,5,6]
    },
 
    
    ],
    
    }
  },
   beforeMount() {
   if(this.currentObj.number === null){ this.currentObj = this.lists[0]}
  },
  methods:{
    listExtrcat(index){
this.currentObj.number = this.lists[index].number;
this.currentObj.arr = this.lists[index].arr;
this.currentObjIndex = index;
console.log(this.currentObj)
},
 studentSelector(){



  let pickedN = Math.floor(Math.random()*this.currentObj.arr.length);
  this.pickedP = this.names[this.currentObj.arr[pickedN]]
  this.currentObj.arr.splice(pickedN,1);

    if( this.currentObj.arr.length === 0){
      this.currentObj.arr = [...this.arr];
      console.log(this.arr)
      
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
