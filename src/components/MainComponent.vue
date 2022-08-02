<template>
  <div
    class="reaction-expectency-container"
    v-if="!reaction_time_expectency_checked"
  >
    <ExpectingComponent
      @hide_expecting_component="update_expecting_component"
    />
  </div>
  <div v-else class="game-template">
    <button>Play</button>
  </div>
</template>

<script>
import ExpectingComponent from "./GameComponents/ExpectingComponent.vue";
import ReactionBoxComponent from "./GameComponents/ReactionBoxComponent.vue";

export default {
  name: "MainComponent",
  components: {
    ExpectingComponent,
    ReactionBoxComponent,
  },
  data() {
    return {
      name: "MainComponent",
      reaction_time_expectency_checked: false,
    };
  },
  methods: {
    update_expecting_component(reaction_time_expectency) {
      this.reaction_time_expectency_checked = true;
      console.log(reaction_time_expectency);
    },
  },
};
</script>

<style scoped>
.game-template {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
