<template>
  <v-container grid-list-xs>
    <v-row>
      <v-col cols="3" v-for="(char, indice) in characters" :key="indice">
        <v-card
          color="grey"
          id="cards"
          @click="
            clickObs(
              char.name,
              char.status,
              char.gender,
              char.image,
              char.species
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
      ></Modal>
    </v-row>
  </v-container>
</template>
<script>
import Modal from "./Modal.vue";
import api from "../services/api";
export default {
  components: {
    Modal,
  },

  data() {
    return {
      characters: [],
      show: false,
      name: "",
      status: "",
      gender: "",
      image: "",
      species: "",
    };
  },
  created() {
    api.then((res) => {
      this.characters = res.data.results;
    });
  },
  methods: {
    clickObs(charName, charStatus, charGender, charImg, charSpecies) {
      this.show = true;
      this.name = charName;
      this.status = charStatus;
      this.gender = charGender;
      this.image = charImg;
      this.species = charSpecies;

      console.log(this.image);
    },
  },
};
</script>
<style scoped>
#cards {
  cursor: pointer;
}
</style>
