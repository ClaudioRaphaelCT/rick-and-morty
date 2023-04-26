<template>
  <v-app>
    <h1 class="text-center" id="title">Rick and Morty</h1>
    <v-divider></v-divider>
    <div>
      <CharCards></CharCards>
    </div>
    <div></div>
    <MyFooter></MyFooter>
  </v-app>
</template>
<script>
import CharCards from "./components/CharCards.vue";
import MyFooter from "./components/MyFooter.vue";
export default {
  components: { CharCards, MyFooter },
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
