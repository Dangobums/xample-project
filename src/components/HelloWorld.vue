<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <DatePicker />
  </div>
</template>

<script setup>
// import { ref } from "vue";
import DatePicker from "@/components/DatePicker";
// const emiteValue = ref("");
// const getValue = (val) => {
//   emiteValue.value = val;
// };
const pros = defineProps({
  msg: String,
});
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
