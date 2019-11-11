<template>
  <div class="digits">
    <div class="showDigits" v-for="(number, index) in 10" :key="index">
      <button @click="dodajUNiz(number-1)" class="button">{{ number-1 }}</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "Digits",
  props: [],
  components: {},
  methods: {
    dodajUNiz(number) {
      this.$emit("dodajUNiz", number);
    }
  }
};
</script>

<style>
.digits {
  width: 250px;
  display: flex;
  flex-wrap: wrap;
  border-radius: 20px;
}
</style>