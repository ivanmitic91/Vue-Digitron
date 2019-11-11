<template>
  <div class="DigWrapper">
    <input type="text" v-model="result" class="showResult" disabled />
    <!-- show digits -->
    <Digits @dodajUNiz="dodajUNiz" />
    <!-- show operators -->
    <Operators @dodajOper="dodajOper" @resetuj="resetuj" v-bind:operators="operators" />
  </div>
</template>

<script>
import Digits from "./Digits.vue";
import Operators from "./Operators.vue";
export default {
  name: "Output",
  props: ["result", "operators"],
  components: {
    Digits,
    Operators
  },
  methods: {
    dodajUNiz(number) {
      this.$emit("dodajUNiz", number);
    },
    dodajOper(mojOper) {
      this.$emit("dodajOperator", mojOper);
    },
    resetuj() {
      this.$emit("resetuj");
    }
  }
};
</script>

<style>
.DigWrapper {
  width: 250px;
  justify-content: space-between;
  display: flex;
  flex-wrap: wrap;
  margin: 50px auto;
  background-color: #ccc;
  padding: 35px;
  border-radius: 20px;
  -webkit-box-shadow: -1px -2px 7px 9px rgba(0, 0, 0, 0.3);
  -moz-box-shadow: -1px -2px 7px 9px rgba(0, 0, 0, 0.3);
  box-shadow: -1px -2px 7px 9px rgba(0, 0, 0, 0.3);
}

.button {
  padding: 15px 25px;
  margin: 0px 0px 12px 17px;
  font-size: 24px;
  text-align: center;
  cursor: pointer;
  outline: none;
  color: #fff;
  background-color: #000;
  border: none;
  border-radius: 15px;
  box-shadow: 0 9px #999;
}

.button:hover {
  background-color: #ccc;
}

.button:active {
  background-color: #eee;
  box-shadow: 0 5px #666;
  transform: translateY(4px);
}

.showResult {
  width: 100%;
  height: 50px;
  background-color: lightblue;
  font-size: 25px;
  line-height: 50px;
  padding-left: 15px;
  margin-bottom: 25px;
}
</style>