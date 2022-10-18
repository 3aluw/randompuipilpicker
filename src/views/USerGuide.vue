<template>
<BlinkingText></BlinkingText>
<section>
    <h1>What is this ?</h1>
<p> In life we need to make some hard decisions, Sometimes, as parents / teachers or managers we need to pick someone to take on a responsibility or to do a hard chore,<br> we need to be fair, fast and more importantly emotionless which is hard (maybe impossible, I don't know) <br> this app will do the job for you, it will pick someone randomly without any prejudice</p>
</section>
<section>
    <h1>How to insert new names ?</h1>
    <p>You can create a new list of names by visiting the <RouterLink to="/newList">create a new list tab</RouterLink> where you can :<br>
     <ul>
    <li>Name your list : a good practice is to give it a meaninful, short name (at max : 18 characters), for example : chess games, math homework checking or dining room cleaning...    </li>
    <li> insert the names : insert the names <strong>separated using a comma"," or insert each name in a new line</strong></li>
    Once done click the "create a new list" button
     </ul> </p>
     <img src="@/assets/creating-a-list-demo.png" alt="demo">
    </section>  
     <section>
        <h1>How to randomly select someone ?</h1>
        <p>
        <ul>
            <li>Head to the<RouterLink to="/"> home page</RouterLink></li>
            <li>click on a list.</li>
            <li>click "pick someone" </li>
         
        </ul>   The app will randomly chose a name for you, the name won't be repeated till all the names had been chosen.
            <br> You can delete/save lists using the buttons on the screen.</p>
    </section>
    <section>
        <h1>What about my data ? where is it saved?</h1>
        <p>All the lists are saved locally on your browser.</p>
    </section>
   <footer>
    <p>For any feedback / suggestion contact me on: <a href="https://twitter.com/Smileydevy"  target="_blank">twitter</a></p>       
    <p> If you really liked the tool, and wanted/able to help, you can  click <a href="https://ko-fi.com/smileydevy"  target="_blank">here</a> </p>
   </footer>

</template>
<script>
import BlinkingText from "../components/BlinkingText.vue";
export default{
    name: "USerGuide",
    components: { BlinkingText }
}
</script>
<style scoped>

section{
text-align: left;
font-family: 'Merriweather', serif;
padding-left: 5%;
}
section>p{
    font-size:1.3rem;
    max-width: 800px;
   
    padding-left: 3rem;
    
}
img{
    display: block;
    border: 1px black solid;
    max-width: 100%;
    margin: 0 auto;;
}
footer{
    background: rgba(202, 160, 250, 0.3);
    min-height: 100px;
 display: flex;
 flex-direction: column;
 justify-content: center;
 color: rgb(12, 12, 12);
 font-family: "Open Sans", sans-serif;
}
a{
    color: #00C9A7;
    text-decoration: none;
}
</style>