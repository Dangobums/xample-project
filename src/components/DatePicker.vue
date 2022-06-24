<template>
  <a-button type="primary" @click="showModal">Open Modal</a-button>
  <a-modal
    v-model:visible="visible"
    title="Tùy chọn khoảng thời gian"
    @ok="handleOk"
    centered
    width="800px"
    height="600px"
  >
    <template #footer>
      <a-button key="confirm" @click="handleOk">Xác nhận</a-button>
    </template>
    <div class="container">
      <div class="model-wrapper model-left">
        <div class="date-wrapper">
          <TimeComponent title="Từ" />
          <div class="date-wrapper__picker">
            <Calender />
          </div>
        </div>
      </div>
      <a-divider
        type="vertical"
        style="height: 340px; background-color: #7cb305; algin-self: center"
      />
      <div class="model-wrapper model-right">
        <div class="date-wrapper">
          <TimeComponent title="Đến" />
          <div class="date-wrapper__picker">
            <Calender />
          </div>
        </div>
      </div>
    </div>
  </a-modal>
</template>
<script setup>
import { ref } from "vue";
import Calender from "./Calender.vue";
import TimeComponent from "./TimeComponent.vue";
const visible = ref(false);
const emit = defineEmits(["name"]);
const showModal = () => {
  visible.value = true;
};
const handleOk = (e) => {
  console.log(e);
  visible.value = false;
};
</script>
<style>
:root {
  --ghtk: #069255;
}
.container {
  display: flex;
  flex-direction: row;
  justify-content: space-evenly;
  height: 100%;
}
.semi-colon {
  color: #ccc;
  margin: 8px;
}
.number-input {
  width: 20px;
}

.title {
  justify-self: start;
}
.model-wrapper {
  display: flex;
  justify-content: center;
}
.model-wrapper.model-right {
  margin-left: 10px;
}
.model-wrapper.model-left {
  margin-right: 10px;
}
.date-wrapper__picker {
  width: 300px;
}
.ant-modal-content {
  border-radius: 12px !important;
}
.ant-modal-title {
  text-align: center;
  font-weight: 700 !important;
  color: #fff !important;
}
.ant-modal-body {
  padding: 0 !important;
}
.ant-modal-header {
  border-radius: 12px 12px 0 0 !important;
  background-color: var(--ghtk) !important;
}
.ant-modal-footer {
  display: flex;
  flex: 1;
  justify-content: center;
  border-top: 0px !important;
}
.ant-modal-footer .ant-btn {
  display: block;
  width: 100%;
  border-radius: 8px;
  font-weight: 700;
  background-color: var(--ghtk);
  color: #fff;
}
.ant-modal-footer .ant-btn:hover {
  display: block;
  width: 100%;
  border-radius: 8px;
  font-weight: 700;
  background-color: var(--ghtk);
  color: #fff;
}
</style>
