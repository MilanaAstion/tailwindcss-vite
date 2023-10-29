<script setup>
import {onMounted, ref } from 'vue';
import axios from 'axios';

const students = ref([]);
onMounted(()=>{
    axios.get("http://34.82.81.113:3000/students").then((response) =>{
      students.value = response.data; 
    });
});
</script>

<template>
  <table class="w-full border-collapse border border-gray-300">
    <thead>
      <tr>
        <th class="bg-gray-200 border border-gray-300 px-4 py-2">Name</th>
        <th class="bg-gray-200 border border-gray-300 px-4 py-2">Group</th>
      </tr>
    </thead>
    <tbody>
      <tr v-for="(stud, index) in students" :key="index" class="bg-white hover:bg-gray-100">
        <td class="border border-gray-300 px-4 py-2 px-10">{{ stud.name }}</td>
        <td class="border border-gray-300 px-4 py-2 px-10">{{ stud.group }}</td>
      </tr>
    </tbody>
  </table>
</template>

<style scoped>
</style>
