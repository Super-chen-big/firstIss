<template>
  <nut-date-picker
      v-model="currentDate"
      title="日期时间选择"
      type="datetime"
      :filter="filter"
      :min-date="minDate"
      :max-date="maxDate"
      @confirm="confirm"
  ></nut-date-picker>
</template>
<script lang="ts">
import {reactive} from 'vue';

export default {
  setup() {
    const currentDate = new Date(2022, 4, 10, 10, 10);
    const classRoomData=reactive({
      name:'一战成硕自习室',
      isOpen:true,
      startTime:'6:00',
      endTime:'23:00',
      address:'河南省郑州市管城回族区区商都路55号亚星投资大厦1510室',
    })
    const filter = (type: string, options) => {
      if (type == 'hour') {
        return options.filter((option) => {
          return Number(option.value)>=Number(classRoomData.startTime.split(':')[0])&&Number(option.value)<=Number(classRoomData.endTime.split(':')[0]);
        });
      }
      return options;
    }
    return {
      currentDate,
      // minDate: new Date(2020, 0, 1),
      // maxDate: new Date(2025, 10, 1),
      filter,
      minDate:new Date(2023,4,4),
      maxDate:new Date(2023,9,10)
    };
  }
};
</script>
