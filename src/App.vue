<template>
  <div id="app">
    <Output
      @dodajUNiz="dodajUNiz"
      @dodajOperator="dodajOperator"
      @resetuj="resetuj"
      v-bind:operators="operators"
      v-bind:result="result"
    />
  </div>
</template>

<script>
import Output from "./components/Output.vue";
/* eslint-disable no-console */
export default {
  data() {
    return {
      myNumber1: "",
      myNumber2: "",
      equal: "",
      expression: "",
      myOperator: undefined,
      operators: ["+", "-", "*", "/"],
      result: ""
    };
  },
  methods: {
    dodajUNiz(number) {
      if (this.myOperator === undefined) {
        this.myNumber1 += number;
      } else if (this.myOperator !== undefined && number !== undefined) {
        this.myNumber2 += number;

        this.expression =
          this.myNumber1 + this.myOperator + this.myNumber2 + " = ";

        let res = eval(this.myNumber1 + this.myOperator + this.myNumber2);

        if (this.myOperator === "/" && this.myNumber2 == 0) {
          this.result = "Deljenje nulom!";
        } else {
          this.result = this.expression + Math.round(res * 100) / 100;
        }
      }
    },

    dodajOperator(operator) {
      this.myOperator = operator;
    },
    resetuj() {
      this.result = 0;
      this.myNumber1 = "";
      this.myNumber2 = "";
      this.myOperator = undefined;
    }
  },
  name: "app",
  components: {
    Output
  }
};
</script>

<style>
</style>
