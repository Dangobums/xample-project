<template>
  <a-config-provider :locale="viVN">
    <a-calendar
      :fullscreen="false"
      :value="date"
      @select="onSelect"
      @panelChange="onPanelChange"
    >
      <template #headerRender>
        <div>
          <a-row type="flex" justify="space-between">
            <a-col>
              <div>
                <arrow-left-outlined />
              </div>
            </a-col>
            <a-col>
              <div>
                <p class="">
                  Tháng {{ selectedValue.format("MM") }}
                  {{ selectedValue.format("YYYY") }}
                </p>
              </div>
            </a-col>
            <a-col>
              <div>
                <arrow-right-outlined />
              </div>
            </a-col>
          </a-row>
        </div>
      </template>
    </a-calendar>
  </a-config-provider>
</template>
<script setup>
import { ref } from "vue";
import { ArrowLeftOutlined, ArrowRightOutlined } from "@ant-design/icons-vue";

import viVN from "ant-design-vue/es/locale/vi_VN";
// import moment, { Moment } from "moment";
import dayjs from "dayjs";
import "dayjs/locale/vi";
// const date = ref(moment("2017-01-25"));
const locale = ref(viVN.locale);
dayjs.locale(locale);
const props = defineProps({
  title: String,
});
const date = ref(dayjs());
const selectedValue = ref(dayjs());

const onSelect = (value) => {
  date.value = value;
  selectedValue.value = value;
  console.log(selectedValue.value);
};
const onPanelChange = (value) => {
  date.value = value;
};

const getMonths = (value) => {
  const localeData = value.localeData();
  const months = [];

  for (let i = 0; i < 12; i++) {
    months.push(localeData.monthsShort(value.month(i)));
  }
};
const getYears = (value) => {
  const year = value.year();
  const years = [];

  for (let i = year - 10; i < year + 10; i += 1) {
    years.push(i);
  }
};
</script>
<style>
.ant-picker-calendar .ant-picker-panel {
  border-top: 0 !important;
}
.ant-picker-date-panel .ant-picker-body {
  padding: 0;
}
.ant-picker-cell-in-view.ant-picker-cell-today .ant-picker-cell-inner::before {
  border: none !important;
}
.ant-picker-cell-in-view.ant-picker-cell-selected .ant-picker-cell-inner {
  border-radius: 50%;
  background-color: var(--ghtk) !important;
}
</style>
