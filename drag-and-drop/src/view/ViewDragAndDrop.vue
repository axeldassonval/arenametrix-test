<template>
  <div class="flex align-center pt-12">
    <DragAndDrop />
    <v-divider></v-divider>
    <v-btn class="my-6" @click="showLocalstorage()"> view data</v-btn>
    <v-divider></v-divider>
    <TableData />
  </div>
</template>

<script setup>
import DragAndDrop from "@/components/DragAndDrop.vue";
import TableData from "@/components/TableData";

const showLocalstorage = () => {
  console.log(JSON.parse(localStorage.getItem("files") || "[]"));
};
</script>

<style></style>
