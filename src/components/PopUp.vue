<template>
  <div class="out">
    <div>
      <span> Thanks you {{ name }} {{ surName }} for submitting the form </span>
      <button @click="close">Close</button>
    </div>
  </div>
</template>

<script>
export default {
  props: ["name", "surName"],
  methods: {
    close() {
      this.$emit("close");
    },
  },
};
</script>

<style scped lang="scss">
.out {
  position: fixed;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: rgba(0, 0, 0, 0.509);
  left: 0;
  top: 0;
  div {
    display: flex;
    justify-content: center;
    align-items: center;
    width: 22vw;
    height: 8vh;
    background-color: rgb(24, 218, 153);
    border-radius: 10px;
    flex-direction: column;
    span {
      text-align: center;
    }
  }
}
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
</style>
