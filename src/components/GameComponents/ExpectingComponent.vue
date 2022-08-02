<template>
  <label for="reaction-expectency"
    >How fast can you hit a box once it pops?</label
  >
  <div class="reaction-expectency-input-button">
    <input
      id="reaction-expectency"
      type="range"
      min="10"
      max="1000"
      placeholder="500ms"
      v-model="reaction_time_expectency"
    />
    <p>{{ reaction_time_expectency }}</p>
  </div>
  <button type="submit" @click="hide_component()">Define</button>
</template>

<script>
export default {
  name: "ExpectingComponent",
  data() {
    return {
      name: "MainComponent",
      reaction_time_expectency: 0,
    };
  },
  methods: {
    hide_component() {
      this.$emit("hide_expecting_component", this.reaction_time_expectency);
    },
  },
};
</script>
