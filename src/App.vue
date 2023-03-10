<template>
  <div class="container">
    <div>
      <input-form />
    </div>
  </div>
</template>

<script>
import InputForm from "./components/InputForm.vue";

export default {
  name: "App",
  components: {
    InputForm,
  },
};
</script>

<style scoped lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.container {
  width: 100vw;
  height: 100vh;

  background-color: rgb(161, 161, 161);
  div {
    width: 30vw;
    height: 30vh;
    border-radius: 10px;
    background-color: gray;
  }
}
</style>
