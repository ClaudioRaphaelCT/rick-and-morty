<template>
  <div class="modal">
    <div class="modal-content">
      <v-card class="meu-card">
        <v-row>
          <img :src="img" max-height="100" max-width="100" />

          <v-card-text>
            <v-card-title primary-title class="text-center">
              {{ name }}</v-card-title
            >
            <v-divider class="mb-3"></v-divider>
            <h3 class="mb-2 ml-2">{{ status }}</h3>
            <h3 class="mb-2 ml-2">{{ gender }}</h3>
            <h3 class="mb-2 ml-2">{{ species }}</h3>
          </v-card-text>
        </v-row>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  props: ["name", "status", "gender", "img", "species"],
  data() {
    return {
      show: true,
    };
  },
};
</script>

<style scoped>
.modal {
  position: fixed;
  z-index: 1;
  left: 0;
  top: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.4);
}
.modal-content {
  background-color: black;
  margin: 15% auto;
  padding: 10px;
  border: 1px solid #888;
  width: 30%;
  cursor: pointer;
}

.meu-card {
  background-color: black;
  color: whitesmoke;
}
</style>
