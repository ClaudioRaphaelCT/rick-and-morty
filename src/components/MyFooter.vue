<template>
  <div class="mt-5">
    <v-footer color="blue-grey-darken-4">
      <v-card flat color="blue-grey-darken-4">
        <v-card-text class="text-center" id="itens">
          <v-btn
            icon
            href="https://www.instagram.com/raphaelcabraal/"
            class="mr-2"
            target="blank"
            title="Instagram"
            ><v-icon>mdi-instagram</v-icon></v-btn
          >
          <v-btn
            icon
            href="https://www.linkedin.com/in/cl%C3%A1udio-raphael-cabral-095738203/"
            class="mr-2"
            target="blank"
            title="Linkedin"
            ><v-icon>mdi-linkedin</v-icon></v-btn
          >
          <v-btn
            icon
            href="https://github.com/ClaudioRaphaelCT"
            class="mr-2"
            target="blank"
            title="Github"
            ><v-icon>mdi-github</v-icon></v-btn
          >
        </v-card-text>
      </v-card>
      <span>&copy; 2023 - Todos os direitos reservados.</span>
    </v-footer>
  </div>
</template>

<script>
import axios from "axios";
export default {
  data() {
    return {
      pages: "",
    };
  },

  mounted() {
    const api = axios.get(
      `https://rickandmortyapi.com/api/character/?page=${this.pages}`
    );
    console.log(api);
    return api;
  },

  methods: {},
};
</script>

<style scoped>
.btns {
  margin-left: 150px;
  margin-top: 10px;
  margin-bottom: 10%;
}

#itens {
  margin-left: 350px;
}
</style>
