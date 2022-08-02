<template>
  <div class="challenge-box">
    <p>here!</p>
  </div>
</template>

<script>
export default {
  name: "ReactionBoxComponent",
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
