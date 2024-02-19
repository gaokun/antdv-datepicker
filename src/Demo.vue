<template>
  <p>本示例展示了ant design vue datepicker在 <b>UTC时区</b> 时显示的异常</p>
  <p>注意: date-picker的value都为带时区的dayjs对象</p>
  <ul>
    <li>
      <span>西一区</span>
      <a-date-picker
        v-model:value="west1DateValue"
        show-time
        placeholder="Select Time"
      />
    </li>
    <li>
      <span>UTC</span>
      <a-date-picker
        v-model:value="utcDateValue"
        show-time
        placeholder="Select Time"
      />
      <span style="color: red; font-weight: bold"
        >应该显示为8点, 实际显示0点</span
      >
    </li>

    <li>
      <span>东一区</span>
      <a-date-picker
        v-model:value="east1DateValue"
        show-time
        placeholder="Select Time"
      />
    </li>
  </ul>
</template>
<script setup>
import { ref } from "vue";
import dayjs from "dayjs";
import utc from "dayjs/plugin/utc";
import timezone from "dayjs/plugin/timezone";

dayjs.extend(utc);
dayjs.extend(timezone);

const time = 1708243200000;

const utcDateValue = ref(dayjs(time).tz("Etc/GMT"));
const east1DateValue = ref(dayjs(time).tz("Etc/GMT-1"));
const west1DateValue = ref(dayjs(time).tz("Etc/GMT+1"));
</script>

<style scoped>
ul {
  li {
    display: grid;
    grid-gap: 10px;
    grid-template-columns: 70px 300px 1fr;
  }
}
</style>
