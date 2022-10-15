<template>
  
    <p>Randomly chose <span class="typed-text"></span><span class="cursor">&nbsp;</span></p>
    </template>
    
    
    <script>
    
    
    
    export default {

      name: 'BlinkingText',
     
      data(){
        return{
         
          textArray: ["a student","a son"," an employee","a sibling","a freind","a DUDE"],
          typingDelay : 200,
          erasingDelay : 100,
          newTextDelay : 2000,
          textArrayIndex:0, 
          charIndex:0,
          }
        },
        mounted(){ 
          this.type()
         if(this.textArray.length) setTimeout(this.type, this.newTextDelay + 250);
        },
        methods:{
          type(){
           const typedTextSpan= document.querySelector(".typed-text");
         const  cursorSpan =  document.querySelector(".cursor");
          console.log(0,cursorSpan)
            if (this.charIndex < this.textArray[this.textArrayIndex].length) {
    if(!cursorSpan.classList.contains("typing")) cursorSpan.classList.add("typing");
    typedTextSpan.textContent += this.textArray[this.textArrayIndex].charAt(this.charIndex);
    this.charIndex++;
    setTimeout(this.type, this.typingDelay);
  } 
  else {
    cursorSpan.classList.remove("typing");
  	setTimeout(this.erase, this.newTextDelay);
  }
          },
          erase(){
            const typedTextSpan= document.querySelector(".typed-text");
         const  cursorSpan =  document.querySelector(".cursor");
	if (this.charIndex > 0) {
    if(!cursorSpan.classList.contains("typing")) cursorSpan.classList.add("typing");
    typedTextSpan.textContent = this.textArray[this.textArrayIndex].substring(0, this.charIndex-1);
    this.charIndex--;
    setTimeout(this.erase, this.erasingDelay);
  } 
  else {
    cursorSpan.classList.remove("typing");
    this.textArrayIndex++;
    if(this.textArrayIndex>=this.textArray.length) this.textArrayIndex=0;
    setTimeout(this.type, this.typingDelay + 1100);
  }
          }

        }
      }
    
      </Script> 
      <style scoped>
  body{
    max-height: 100px;
    font-family: 'Montserrat', sans-serif;

  }
  .cont{
    position: relative;
  }
  p{
display: inline-block;
    font-size: 2rem;
  padding: 0.5rem;
  font-weight: bold;
  letter-spacing: 0.1rem;
  
  }
 
  .typed-text{
    color:#845EC2;
    font-size: 2rem;
  }
  .cursor{
    display: inline-block;
  background-color: #ccc;
  margin-left: 0.1rem;
  width: 2px;
  height: 2rem;

    bottom:0;
  animation: blink 1s infinite;
  }
  @keyframes blink {
  0%  { background-color: rgb(0, 0, 0); }
  49% { background-color: rgb(0, 0, 0); }
  50% { background-color: transparent; }
  99% { background-color: transparent; }
  100%  { background-color: rgb(0, 0, 0); }
}
.cursor.typing{
    animation: none;
}
      </style>