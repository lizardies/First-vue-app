<template>
  <div class="poll-page">
    <form red="form">
      <div class="poll-container">
        <table class="table">
          <tbody>
            <td>question</td>
            <td><input v-model="question" type="text" /></td>

            <div class="answers">
              <td>answers</td>
              <tr v-for="row in rows" :key="row.id">
                <td><input type="text" v-model="row.title" /></td>
                <td>
                  <a v-on:click="removeElement(row)" style="cursor: pointer"
                    >x</a
                  >
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
        <div></div>
      </div>
    
    </form>
  </div>

   
</template>

<script>
import uniqueId from "lodash.uniqueid";

export default {
  name: "Poll",
  data() {
    return {
      question:'',
      rows: [{title: "", id: uniqueId("answer-") }],
    };
  },
  methods: {
    addRow: function () {
      console.log(this.rows)
      this.rows.push({title: this.title, id: uniqueId("answer-") });
    },
    removeElement: function (row) {
      var index = this.rows.indexOf(row);
      this.rows.splice(index, 1);
    },
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
  float: left;
  display: block;
  width: 100vw;
}

.showBut span {
  display: none;
}
</style>
