<template>
  <h1 class="title">Challenge Your Reaction</h1>
  <div class="main">
    <MainComponent />
  </div>
</template>

<script>
import MainComponent from "./components/MainComponent.vue";

export default {
  name: "App",
  components: {
    MainComponent,
  },
};
</script>

<style scoped>
.main {
  display: flex;
  justify-content: center;

  padding: 10rem;
  height: 50vh;
}

.title {
  display: inline;
  background-color: rgba(234, 255, 220, 1);
  /* background-color: var(--mainTextColor); */
  box-shadow: 0 0 50px 10px var(--mainTextColor);
  color: var(--coolBlack);
  border: 1px solid var(--coolBlack);
  border-radius: 10rem;
  padding: 1rem;
}
</style>
