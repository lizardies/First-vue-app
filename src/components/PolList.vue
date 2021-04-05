<template>
<div>
    <h1>hi</h1>
<Poll />

        <button id="createPoll" class="button btn-primary" v-on:click="createPoll()">Create 
      </button> 

 <div class="polls-container">
      <ul style="list-style-type: none">
        <li
          v-for="poll in existingPolls"
          v-bind:key="poll.id"
          v-bind:title="poll.question"
        >
          <span> {{ poll.question }} </span><br>
          <ul style="list-style-type:none;">
        <li
      v-for="(answer) in poll.answers"
      v-bind:key="answer.title"
      v-bind:title="answer.title"
    ><button  class="showBut"  > {{answer.title}} 


       </button> 

    </li>
    </ul>
    <br>
        </li>
      </ul>
    </div>
    

    
    </div>
</template>

<script>
import Poll from "./Poll.vue";
import uniqueId from "lodash.uniqueid";


export default {
  name: "PolList",
  components: {
     Poll,
  },
  data() {
      return{
        existingPolls: [
        {
          id: uniqueId("poll-"),
          question: "what is your favourite color?",
           answers : [
             {title:'yellow', id:uniqueId('temp-'), perc:'10'},
             {title:'orange', id:uniqueId('temp-'),  perc:'10'},
             {title:'purple', id:uniqueId('temp-'), perc:'80'}]
        }]
      } }
      ,
  methods: {
    createPoll: function () {
        console.log();
        this.existingPolls.push(
             {
          id: uniqueId("poll-"),
          question: "what is your favourite color?",
           answers : [
             {title:'yellow',id:uniqueId('temp-'),  perc:'20'},
             {title:'orange',id:uniqueId('temp-'),  perc:'30'},
             {title:'purple', id:uniqueId('temp-'),  perc:'50'}]
        }
        )
    },

  }
}

</script>

<style>

</style>
