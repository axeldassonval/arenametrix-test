<template>
  <div class="d-flex justify-center">
    <v-card elevation="24" class="my-6 card" width="900">
      <v-card-title>
        <strong> Dépots de <span style="color: #31baa8">fichier</span> </strong>
      </v-card-title>
      <v-spacer></v-spacer>
      <v-divider></v-divider>
      <v-card-text>
        <v-row class="d-flex justify-space-around mb-6 align-center display-in">
          <v-col cols="6" class="d-flex align-center">
            <div class="file-dropzone" ref="dropzone">
              <input type="file" id="fileInput" ref="fileInput" />
              <p>Click or drag and drop files here</p>
            </div>
          </v-col>
          <v-col cols="6" class="align-center">
            <v-text-field
              v-model="informationsFile.label"
              label="Libellé"
            ></v-text-field>
            <v-select
              v-model="informationsFile.category"
              label="Category"
              :items="categoryItems"
            ></v-select>
            <v-select
              v-model="informationsFile.recipients"
              chips
              label="Destinataires"
              :items="recipientsItems"
              multiple
            ></v-select>
            <v-textarea
              v-model="informationsFile.comment"
              label="commentaire"
            ></v-textarea>
          </v-col>
        </v-row>
      </v-card-text>
      <v-divider></v-divider>
      <v-card-actions class="d-flex justify-space-between">
        <v-btn @click="validateData()" class="btn-arenametrix">Envoyer</v-btn>
        <v-btn @click="cancel()" class="cancel-btn">Annuler</v-btn>
      </v-card-actions>
    </v-card>
  </div>
</template>

<script setup>
import { ref, onMounted } from "vue";

const fileInput = ref(null);
const dropzone = ref(null);
const categoryItems = [
  "Proposition commerciale",
  "Présentation",
  "Document marketing",
  "Réponse AO",
  "Data",
  "Signature du contrat",
  "Formulaire d'engagement",
  "Devis",
  "Renouvellement de contrat",
  "Rapport",
  "Proposition de renouvellement",
  "Autre",
];
const recipientsItems = [
  "Direction",
  "Comptabilité",
  "Commercial",
  "Marketing",
];

const informationsFile = ref({
  name: null,
  label: null,
  category: null,
  createdBy: null,
  createdDate: null,
  recipients: [],
  status: null,
  dateOfDownload: null,
  fileSize: null,
  comment: null,
});

function validateData() {
  if (fileInput.value.files.length === 0 || informationsFile.value === "") {
    return;
  }

  informationsFile.value.name = fileInput.value.files[0].name;
  informationsFile.value.createdBy = "Admin";
  informationsFile.value.fileSize = fileInput.value.files[0].size;
  informationsFile.value.createdDate = new Date().toLocaleDateString();

  let files = localStorage.getItem("files");
  files = files ? JSON.parse(files) : [];
  files.push(informationsFile.value);
  localStorage.setItem("files", JSON.stringify(files));
}

function cancel() {
  informationsFile.value = {
    label: "",
    category: "",
    recipients: [],
    comment: "",
  };
  dropzone.value = null;
  fileInput.value.files = null;
}

const handleDragOver = (event) => {
  event.preventDefault();
  dropzone.value.classList.add("active");
};

const handleDragLeave = () => {
  dropzone.value.classList.remove("active");
};

const handleDrop = (event) => {
  event.preventDefault();
  dropzone.value.classList.remove("active");

  const files = event.dataTransfer.files;
  if (files.length > 0) {
    fileInput.value.files = files;
  }
};

onMounted(() => {
  // Attach event listeners after elements are mounted
  dropzone.value.addEventListener("dragover", handleDragOver);
  dropzone.value.addEventListener("dragleave", handleDragLeave);
  dropzone.value.addEventListener("drop", handleDrop);
});
</script>

<style scoped></style>
