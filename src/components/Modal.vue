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
            <h3 v-if="status == 'Alive'" class="mb-2 ml-2">
              <v-icon color="green">mdi-circle</v-icon> {{ status }}
            </h3>
            <h3 v-if="status == 'Dead'" class="mb-2 ml-2">
              <v-icon color="red">mdi-skull-scan</v-icon> {{ status }}
            </h3>
            <h3
              v-if="status !== 'Alive' && status !== 'Dead'"
              class="mb-2 ml-2"
            >
              <v-icon color="yellow">mdi-help-circle-outline</v-icon>
              {{ status }}
            </h3>

            <h3 class="mb-2 ml-2">
              <v-icon color="blue" v-if="gender == 'Male'"
                >mdi-gender-male</v-icon
              >
              <v-icon color="pink" v-if="gender == 'Female'"
                >mdi-gender-female</v-icon
              >
              <v-icon
                color="yellow"
                v-if="gender !== 'Female' && gender !== 'Male'"
                >mdi-help-circle</v-icon
              >
              {{ gender }}
            </h3>
            <h3 class="mb-2 ml-2">
              <v-icon v-if="species == 'Alien'" color="green">mdi-alien</v-icon>
              <v-icon v-else-if="species == 'Human'" color="grey"
                >mdi-human</v-icon
              >
              <v-icon v-else color="grey">mdi-account-question</v-icon>
              {{ species }}
            </h3>
            <v-divider class="mt-2 mb-2"></v-divider>
            <h3 class="text-center mt-3 mb-5">Location</h3>

            <v-card-subtitle color="white" class="text-center">{{
              location
            }}</v-card-subtitle>
          </v-card-text>
        </v-row>
      </v-card>
    </div>
  </div>
</template>

<script>
export default {
  props: ["name", "status", "gender", "img", "species", "location"],
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
  width: 55%;
  cursor: pointer;
}

.meu-card {
  background-color: black;
  color: whitesmoke;
}
</style>
