<!-- 6- Creating Thhis Component -->

<template>
  <!-- 13- Attach the value in step 12 -->
  <!-- 23- We call stop_timer function by hitting the challenge-box -->
  <div class="challenge-box" v-if="show_box" @click="stop_timer">
    <span>click here!</span>
  </div>
</template>

<script>
export default {
  name: "ReactionBoxComponent",
  // 7- Defining props and adding delay value
  // 25- adding is_playing value for the reason in step 24
  props: ["delay", "is_playing"],
  data() {
    return {
      // 12- Adding a boolean variable to show the box only when it is true
      show_box: false,
      // 19- We define 2 variables for tracking the time it takes from the users until they click
      timer: null,
      reaction_time: 0,
    };
  },
  // 14- Creating mounted hook to start a timer when the component is mounted
  mounted() {
    // 15- Attach delay props that the timer starts after the delay time
    setTimeout(() => {
      // 16- Set show_box to true that is shows the box after the delay time
      this.show_box = true;
      // 18 we call start_timer method here that it starts counting after the delay time
      this.start_timer();
    }, this.delay);
  },
  methods: {
    // 17- This method will be called immediately after the box pops-up to start the timer
    start_timer() {
      // 20- The reason that we store setinterval in a variale is that we can clear it after we're done
      this.timer = setInterval(() => {
        // 21- This increases reaction time every 10ms
        this.reaction_time += 10;
      }, 10);
    },
    // 22- We defin a function to stop the timer from running and also clearing the interval each time we stop the timer
    stop_timer() {
      clearInterval(this.timer);
      // 26- We need to send the reaction_time to parent component for showing the result
      this.$emit("end_game", this.reaction_time);
    },
  },
};
</script>

<style scoped>
/* ReactionBox Component stylng */

.challenge-box {
  width: 400px;
  height: 200px;
  margin: 0 auto;

  display: flex;
  justify-content: center;
  align-items: center;

  background-color: var(--mainTextColor);
  color: var(--coolBlack);
  padding: 1rem;

  border: 1px solid var(--coolBlack);
  border-radius: 0.5rem;
}
</style>
