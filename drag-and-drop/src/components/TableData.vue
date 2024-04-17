<template>
  <div class="d-flex justify-center py-6 bg-arenametrix">
    <div class="table-contenent">
      <div ref="table"></div>
    </div>
  </div>
</template>

<script setup>
import { ref, reactive, onMounted } from "vue";
import { TabulatorFull as Tabulator } from "tabulator-tables";
const table = ref(null); //reference to your table element
const tabulator = ref(null); //variable to hold your table
const tableData = reactive([JSON.parse(localStorage.getItem("files") || "[]")]); //data for table to display

onMounted(() => {
  //instantiate Tabulator when element is mounted
  tabulator.value = new Tabulator(table.value, {
    data: tableData.value,
    reactiveData: true,
    height: "311px",
    columns: [
      { title: "Nom", field: "name" },
      {
        title: "Libellé",
        field: "label",
      },
      { title: "Categorie", field: "category" },
      { title: "Date du dépot", field: "createdDate", hozAlign: "center" },
      { title: "créer par", field: "createdBy" },
      {
        title: "Destinataires",
        field: "recipients",
      },
      { title: "Statut", field: "status", hozAlign: "center" },
      {
        title: "Date de telechargement",
        field: "dateOfDownload",
        hozAlign: "center",
      },
      { title: "Taille du fichier", field: "fileSize", hozAlign: "center" },
      { title: "Action", field: "action", hozAlign: "center" },
    ],
  });
  return { tabulator, table };
});
</script>

<style scoped></style>
