<template>
    <div v-for="task in filteredTasks" :key="task.id" :style="getTaskStyle(task)" class="absolute left-1/2 bg-purple-700 text-white w-10/12 rounded-md transform -translate-x-1/2 pt-1">
      <p class="text-left text-lg font-bold pl-1">{{ task.title }}</p>
      <p class="taskMembersName text-left text-xs pl-1">{{ getMembersString(task.members) }}</p>
      <div class="grid grid-cols-2 mt-2">
        <div class="col-span-1 flex pl-1">
          <div  v-for="member in task.members" :key="member.id">
            <img :src="member.avatar_url" alt="Member Image" class="w-7 rounded-full h-auto border-2 border-white">
          </div>
        </div>
      <div class="col-span-1">
        <p class="text-right text-sm pr-2">{{task['start-time'].toString()}} - {{task['end-time'].toString()}}</p>
      </div>
      </div>

    </div>
</template>

<script>
import db from '@/json/db.json';
import moment from 'moment';

export default {
  name: 'CalendarGrid',
  props: {
    selectedDay: {
      type: moment,
      default: null,
    },
  },
  data() {
    return {
      dbData: [],
      startTimeInFloat: null,
      endTimeInFloat: null,
    };
  },
  computed: {
    filteredTasks() {
      return this.dbData.filter(task =>
        moment(task.date, "DD/MM/YYYY").isSame(this.selectedDay, 'day')
      );
    },
  },
  methods: {
    timeInFloat(time) {
      let [hour, minute] = time.split(':');
      return (parseInt(hour) + parseInt(minute) / 60).toFixed(2);
    },
    getTaskStyle(task) {
      const startTime = this.timeInFloat(task['start-time']);
      const endTime = this.timeInFloat(task['end-time']);
      return {
        top: `${startTime * 64}px`,
        height: `${(endTime - startTime) * 64}px`,
      };
    },
    getMembersString(members) {
      return members.map(member => member.name).join(", ");
    },
  },
  created() {
    this.dbData = db.tasks;
  },
};
</script>

<style scoped>
.taskMembersName {
  margin-top: -8px;
}
</style>