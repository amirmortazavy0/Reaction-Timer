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
    <div class="expectency-double-check">
      <h3>What you expect of yourself {{ reaction_time_expectency }} ms?!</h3>
      <a
        href="#"
        @click="
          reaction_time_expectency_checked = false;
          is_playing = false;
        "
        >Change Expectency</a
      >
    </div>
    <div class="hit-zone">
      <!-- 8- importing ReactionBoxComponent in parent component -->
      <!-- 9- We onlu show this component while playing -->
      <!-- 10- Passing data to delay props in the component -->
      <!-- 24- We need to pass is_playing value for replacing "click here!" with the reaction_time after stopping the timer -->
      <!-- 27- Attach emmited event and trigger another function -->
      <ReactionBoxComponent
        v-if="is_playing"
        :delay="delay"
        :is_playing="is_playing"
        @end_game="show_result"
      />
      <!-- 31- showing the final result -->
      <h1 v-else>{{ final_reaction_time }}</h1>
      <!-- 1- Definign the button and start function -->
      <!-- 11- Disable the button while playing -->
      <button @click="start" :disabled="is_playing">Play</button>
    </div>
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
    ReactionBoxComponent,
  },
  data() {
    return {
      name: "MainComponent",
      reaction_time_expectency_checked: false,
      reaction_time_expectency: null,
      // 2- Defining a variable to check  if the game is going on or not
      is_playing: false,
      // 4- Defining a variable for delay time from clicking the play button to the time the box pops-up
      delay: null,
      // 29- We define a variable to store the final result
      final_reaction_time: null,
    };
  },
  methods: {
    update_expecting_component(reaction_time_expectency) {
      this.reaction_time_expectency_checked = true;
      this.reaction_time_expectency = reaction_time_expectency;
    },
    start() {
      // 5- Using Math library for generating random delay time
      this.delay = 2000 + Math.random() * 5000;
      // 3- Change the playig status by clicking on the play button
      this.is_playing = true;
    },
    show_result(reaction_time) {
      // 28- Setting is_playing to false to finish the game
      this.is_playing = false;
      // 30- Passing reaction_time to the final_reaction_time
      this.final_reaction_time = reaction_time;
    },
  },
};
</script>

<style scoped>
.game-template {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}

.expectency-double-check {
  display: flex;
  align-items: center;
  gap: 1rem;
}

.hit-zone {
  display: flex;
  flex-direction: column;
  gap: 1rem;
}
</style>
