<template>
  <HeaderArenametrix />
  <ViewDragAndDrop />
  <FooterArenametrix />
</template>

<script setup>
import ViewDragAndDrop from "@/view/ViewDragAndDrop.vue";
import HeaderArenametrix from "@/components/HeaderArenametrix.vue";
import FooterArenametrix from "@/components/FooterArenametrix";
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
