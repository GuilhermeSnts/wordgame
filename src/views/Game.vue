<template>
  <div class="home">
    <h1 class="title">The Word Game</h1>

    <div class="board col">
      <div class="row" v-for="(row, index) in table" :key="index">
        <div v-for="(letter, index) in row" :key="index">
          <PushButton :letter="letter" />
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import PushButton from "@/components/PushButton";
export default {
  name: "home",
  components: {
    PushButton
  },

  data: () => ({
    dicionary: [
      "abacaxi",
      "celular",
      "genipapo",
      "jovem",
      "folha",
      "carvalho",
      "sofa"
    ],
    alphabet: [
      "a",
      "b",
      "c",
      "d",
      "e",
      "f",
      "g",
      "h",
      "i",
      "j",
      "k",
      "l",
      "m",
      "n",
      "o",
      "p",
      "q",
      "r",
      "s",
      "t",
      "u",
      "v",
      "w",
      "x",
      "y",
      "z"
    ],
    totalWords: 4,
    selectedWords: [],
    table: []
  }),
  methods: {
    generateWords() {
      for (let index = 0; index < this.totalWords; index++) {
        let sort = Math.round(Math.random() * (this.dicionary.length - 1));
        this.selectedWords.push(this.dicionary[sort]);
      }
    },
    generateTable() {
      let table = [];
      while (table.length < 10) {
        let row = [];
        while (row.length < 10) {
          let letter = this.alphabet[Math.round(Math.random() * 25)];
          let upperCase = letter.toUpperCase();
          row.push(upperCase);
        }
        table.push(row);
      }
      this.table = table;
      this.selectedWords.forEach((c, i) => {
        this.horizontalInsertion(this.selectedWords[i]);
      });
    },
    horizontalInsertion(word) {
      let randomCol = Math.round(Math.random() * 10);
      let splittedWord = word.split("").map(c => c.toUpperCase());
      let startPosition = Math.round(Math.random() * 10) - word.length;

      if (startPosition < 0) startPosition = 0;

      let row = this.table[randomCol];

      row.splice(startPosition, splittedWord.length, splittedWord);

      let flatRow = row.flat();
      this.table[randomCol] = flatRow;
    }
  },
  mounted() {
    this.generateWords();
    this.generateTable();
  }
};
</script>

<style lang="sass" scoped>
$wenge: #626151

.home
  padding: 10px
  display: flex
  flex-flow: column
  align-items: center
  justify-content: center

.title
  color: $wenge


.col
  display: flex
  flex-flow: column

.row
  display: flex
  flex-flow: row
</style>
