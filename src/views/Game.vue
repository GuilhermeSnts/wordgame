<template>
  <div class="home">
    <h1>the project begins</h1>
    <p>words: {{ selectedWords }}</p>
    <p>table:</p>

    <div class="col">
      <div class="row" v-for="(row, index) in table" :key="index">
        <div class="letter" v-for="(letter, index) in row" :key="index">
          {{ letter }}
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "home",
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

<style scoped>
.home {
  padding: 10px;
}
.col {
  display: flex;
  flex-flow: column;
}
.row {
  display: flex;
  flex-flow: row;
}
.letter {
  padding: auto;
  margin: 2px;
  width: 30px;
  height: 30px;
  text-align: center;
  border: 1px solid grey;
  border-radius: 2px;
  background: rgb(248, 248, 248);
}
.letter:hover {
  background: lightgrey;
}
</style>
