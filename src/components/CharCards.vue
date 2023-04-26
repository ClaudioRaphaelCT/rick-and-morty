<template>
  <v-container grid-list-xs>
    <v-text-field
      name="name"
      label="Search your Character"
      color="teal-accent-4"
      v-model="search"
    ></v-text-field>
    <v-row>
      <v-col cols="3" v-for="(char, indice) in filteredSearch" :key="indice">
        <v-card
          color="grey"
          id="cards"
          @click="
            clickObs(
              char.name,
              char.status,
              char.gender,
              char.image,
              char.species,
              char.location.name
            )
          "
        >
          <v-card-title primary-title>
            {{ char.name }}
          </v-card-title>
          <v-img :src="char.image" alt="" />
        </v-card>
      </v-col>
      <Modal
        v-if="show"
        @click="show = false"
        :name="name"
        :status="status"
        :gender="gender"
        :img="image"
        :species="species"
        :location="location"
      ></Modal>
    </v-row>
    <v-row class="btns">
      <v-btn color="teal-accent-4" class="mr-2" @click="handleBack">Back</v-btn>
      <v-btn color="blue-grey-darken-3" class="mr-2" @click="handlePages(1)"
        >1</v-btn
      >
      <v-btn color="blue-grey-darken-3" class="mr-2" @click="handlePages(2)"
        >2</v-btn
      >
      <v-btn color="blue-grey-darken-3" class="mr-2" @click="handlePages(3)"
        >3</v-btn
      >
      <v-btn color="blue-grey-darken-3" class="mr-2" @click="handlePages(4)"
        >4</v-btn
      >
      <v-btn color="blue-grey-darken-3" class="mr-2" @click="handlePages(5)"
        >5</v-btn
      >
      <v-btn color="teal-accent-4" class="mr-2" @click="handleNext">Next</v-btn>
      <h3 class="page">Page: {{ pages }}</h3>
    </v-row>
  </v-container>
</template>
<script>
import Modal from "./Modal.vue";
import api from "../services/api";
import axios from "axios";

export default {
  components: {
    Modal,
  },

  data() {
    return {
      characters: [],
      search: "",
      pages: 1,
      show: false,
      name: "",
      status: "",
      gender: "",
      image: "",
      species: "",
      location: "",
    };
  },

  mounted() {
    api.then((res) => {
      this.characters = res.data.results;
    });
  },

  computed: {
    filteredSearch() {
      return this.characters.filter((e) => {
        return e.name.toLowerCase().includes(this.search.toLowerCase());
      });
    },
  },

  methods: {
    clickObs(
      charName,
      charStatus,
      charGender,
      charImg,
      charSpecies,
      charLocation
    ) {
      this.show = true;
      this.name = charName;
      this.status = charStatus;
      this.gender = charGender;
      this.image = charImg;
      this.species = charSpecies;
      this.location = charLocation;
      console.log(this.location);
    },
    handlePages(page) {
      this.pages = page;
      const api = axios.get(
        `https://rickandmortyapi.com/api/character/?page=${this.pages}`
      );
      api.then((res) => {
        this.characters = res.data.results;
      });
    },
    handleBack() {
      this.pages = this.pages - 1;
      if (this.pages < 1) {
        this.pages = 1;
      }
      const api = axios.get(
        `https://rickandmortyapi.com/api/character/?page=${this.pages}`
      );
      api.then((res) => {
        this.characters = res.data.results;
      });
    },
    handleNext() {
      this.pages = this.pages + 1;
      const api = axios.get(
        `https://rickandmortyapi.com/api/character/?page=${this.pages}`
      );
      api.then((res) => {
        this.characters = res.data.results;
      });
    },
  },
};
</script>
<style scoped>
#cards {
  cursor: pointer;
}

.page {
  margin-left: 27%;
  margin-top: 3px;
}
</style>
