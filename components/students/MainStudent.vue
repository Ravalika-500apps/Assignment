<template>
  <div>
    <StudentsListStudent
      @slidebar="addSlidebar"
      @editSlidebar="editSlidebar"
      @deleteFloors="deleteFloors"
      :floorData="getFloorData"
    ></StudentsListStudent>
    <div v-if="is_open" :key="render">
      <StudentsAddStudent
       @add="addStudent"
        :floorData="getFloorData"
        :is_open="is_open"
      ></StudentsAddStudent>
    </div>
    <div v-if="isOpen" :key="editRender">
      <StudentsEditStudent
        :floorData="getFloor"
        @editFloors="editFloors"
      ></StudentsEditStudent>
    </div>
  </div>
</template>
<script setup lang='ts'>
import { Body } from "nuxt/dist/head/runtime/components";
import { ref } from "vue";

const getFloorData = ref([]);
const is_open = ref(false);
const is_open1 = ref(false);
const render = ref(0);
const editRender = ref(0);
const getFloor = ref({});
const isOpen = ref(false);
const students=ref([])
// for getting data from get call

// add call for adding the candidates



// Add openSlidebar data
const addSlidebar = () => {
  is_open.value = true;
  render.value++;
};



// delete the floors
const addStudent = (data: object) => {
      students.value.push(data);
      localStorage.setItem("students", JSON.stringify(students.value));
}



</script>