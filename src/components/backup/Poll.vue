<template>
<div class="poll-page">
<form>
  <div class="poll-container">
    <table class="table">
      <tbody>
   
        <td>question</td>
        <td><input v-model="rows.question" type="text" /></td>

        <div class="answers">
          <td>answers</td>
          <tr v-for="row in rows" :key="row.id">
            <td><input type="text" v-model="row.title" /></td>
            <td>
              <a v-on:click="removeElement(row)" style="cursor: pointer">x</a>
            </td>
          </tr>
        </div>

      </tbody>
    </table>
    <div>
      <button id="addRow" class="button btn-primary" @click="addRow">
        Add Answer
      </button>
    </div>
  <div>
      <button id="createPoll" class="button btn-primary" v-on:click="createPoll(rows)">Create 
      </button>
    </div>


  </div>
</form>



  <div class="polls-container">
    <ul style="list-style-type:none;">
    <li
      
      v-for="(poll) in existingPolls"
      v-bind:key="poll.id"
      v-bind:title="poll.question"
    ><span> {{poll.question}} </span> 
        <!-- <ul style="list-style-type:none;">
        <li
      is="poll-item"
      v-for="(answer) in poll.answers"
      v-bind:key="answer.title"
      v-bind:title="answer.title"
    ><button  class="showBut" > {{answer.title}} 


       </button> <br>

    </li>
    </ul> -->
    </li>
  </ul>
  </div>

  </div>
</template>

<script>
import uniqueId from "lodash.uniqueid";

export default {
  name: "Poll",
  data() {
    return {
      existingPolls: [{
        id: uniqueId("poll-"),
        question: 'what is your favourite color?'
        // answers : [
        //   {title:'yellow', id:'d1'},
        //   {title:'orange', id:'d2'},
        //   {title:'purple', id:'d3'}]  
      }],
      rows: [{ question:"", title: "", id: uniqueId("answer-") }],
    };
  },
  methods: {
    addRow: function () {
      this.rows.push({ question:"", title: "", id: uniqueId("answer-") });
    },
    removeElement: function (row) {
      var index = this.rows.indexOf(row);
      this.rows.splice(index, 1);
    },
    createPoll: function() {
     // var questionGet = row.question;
      console.log(this.existingPolls.question)

      console.log("something happening");
    }
  },
};
</script>

<style>
h3 {
  margin-bottom: 5%;
}

td {
  display: block;
  float: left;
}

#addRow {
  position: absolute;
  left: 25%;
}

div {
  float:left;
  display: block;
  width:100vw;
}

.showBut span {
  display: none;
}
</style>
