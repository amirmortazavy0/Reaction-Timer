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
  align-items: center;

  padding: 1rem;
  height: 50vh;
}

.title {
  text-shadow: 1px 1px 30px var(--mainTextColor);
  color: var(--coolBlack);
}
</style>
