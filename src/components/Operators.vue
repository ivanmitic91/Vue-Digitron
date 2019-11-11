<template>
  <div class="operators">
    <div class="showOperators" v-for="(mojOper) in operators" :key="mojOper">
      <button @click="dodajOper(mojOper)" class="button operators">{{ mojOper }}</button>
    </div>
    <button class="button reset" @click="resetuj()">Clear</button>
  </div>
</template>

<script>
export default {
  name: "Operators",
  props: ["operators"],
  components: {},
  methods: {
    dodajOper(mojOper) {
      this.$emit("dodajOper", mojOper);
    },
    resetuj() {
      this.$emit("resetuj");
    }
  }
};
</script>

<style scoped>
.operators {
  display: flex;
  flex-direction: row;
  flex-wrap: wrap;
}
.button {
  background-color: orange;
}

.reset {
  background-color: red;
  margin-left: 24px;
}
</style>