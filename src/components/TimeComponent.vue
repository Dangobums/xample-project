<template>
  <div class="time-wrapper">
    <div class="time-wrapper__title">
      <div class="title">{{ title }}</div>
    </div>
    <div class="time-wrapper__time">
      <a-input-number
        v-model:value="value"
        size="small"
        :min="0"
        :step="1"
        :max="23"
      />
      <span class="semi-colon">:</span>
      <a-input-number
        v-model:value="value"
        size="small"
        :min="0"
        :step="1"
        :max="60"
      />
    </div>
  </div>
</template>
<script setup>
import { ref } from "vue";
const props = defineProps({
  title: String,
});
const value = ref("01");
</script>

<style>
.time-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  padding: 12px;
}
.time-wrapper__title {
  margin-right: auto;
  font-weight: 700;
  justify-self: flex-start;
  color: rgb(165, 155, 155);
}
.time-wrapper__time .ant-input-number {
  width: 4em;
  padding-top: 8px;
}
.time-wrapper__time .ant-input-number-handler-wrap {
  opacity: 1;
}
.time-wrapper__time {
  flex: 1;
  display: flex;
  justify-content: center;
  transform: translateX(5px);
}
</style>
