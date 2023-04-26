<template>
  <v-app>
    <h1 class="text-center" id="title">Rick and Morty</h1>
    <v-divider></v-divider>
    <div>
      <CharCards> </CharCards>
    </div>
    <div></div>
  </v-app>
</template>
<script>
import CharCards from "./components/CharCards.vue";
export default {
  components: { CharCards },
  data() {
    return {};
  },
};
</script>
<style>
#title {
  background-color: black;
  color: white;
}
</style>
