<template>
  <div class="container">
    <div v-if="this.valid">
      <pop-up :name="name" :surName="surName" @close="close" />
    </div>
    <form>
      <span
        >Name
        <input
          :value="name"
          @input="name = $event.target.value"
          :class="{ wrong: /[0-9]/.test(this.name) }"
      /></span>
      <span
        >Surname
        <input
          :value="surName"
          @input="surName = $event.target.value"
          :class="{ wrong: /[0-9]/.test(this.surName) }"
          type="text"
      /></span>
      <span
        >Birth Date
        <input
          :class="{
            wrong:
              new Date(this.date).getFullYear() >= new Date().getFullYear() ||
              new Date(this.date).getFullYear() < 1900,
          }"
          :value="date"
          @input="date = $event.target.value"
          type="date"
      /></span>
      <span
        >Sex
        <select>
          <option>М</option>
          <option>Ж</option>
        </select></span
      >
      <span
        >Phone number
        <input
          :value="phone"
          @input="phone = $event.target.value"
          :class="{
            wrong:
              (/[a-zA-Z]/.test(this.phone) || this.phone.length !== 11) &&
              this.phone !== '',
          }"
      /></span>
      <span
        >Email
        <input
          :value="email"
          @input="email = $event.target.value"
          :class="{
            wrong:
              !/(.+)@(.+){2,}\.(.+){2,}/.test(this.email.toLowerCase()) &&
              this.email !== '',
          }"
      /></span>
      <div>
        <span>Do you Agree to submit your infos</span> <br />
        <label>Да <input value="true" v-model="radio" type="radio" /> </label>
        <label>Нет <input value="false" v-model="radio" type="radio" /> </label>
      </div>
    </form>
    <div class="buttons">
      <button @click="validate()">Submit</button>
      <button @click="reset()">Reset</button>
    </div>
  </div>
</template>

<script>
import PopUp from "./PopUp.vue";
export default {
  components: { PopUp },
  data() {
    return {
      name: "",
      surName: "",
      date: "",
      Sex: "",
      phone: "",
      email: "",
      radio: false,
      valid: false,

      validName: /[0-9]/.test(this.name),
      validSurname: !/[0-9]/.test(this.surName),
      validdate:
        !new Date(this.date).getFullYear() >= new Date().getFullYear() ||
        !new Date(this.date).getFullYear() < 1900,
    };
  },
  methods: {
    close() {
      this.valid = false;
      this.reset();
    },
    validate() {
      if (
        !/[0-9]/.test(this.name) &&
        !/[0-9]/.test(this.surName) &&
        !(
          new Date(this.date).getFullYear() >= new Date().getFullYear() ||
          new Date(this.date).getFullYear() < 1900
        ) &&
        (/(.+)@(.+){2,}\.(.+){2,}/.test(this.email.toLowerCase()) ||
          this.email === "") &&
        !(/[a-zA-Z]/.test(this.phone) || this.phone.length !== 11)
      ) {
        if (this.radio) {
          this.valid = true;
        } else {
          alert("You must agree to submit information");
        }
      } else {
        alert("Enter valid data");
      }
    },
    reset() {
      this.name = "";
      this.surName = "";
      this.date = "";
      this.phone = "";
      this.email = "";
      this.radio = false;
      this.valid = false;
    },
  },
};
</script>

<style scped lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
.wrong {
  border-color: red;
}
.container {
  position: absolute;
  width: 100vw;
  height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  flex-direction: column;
  form {
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: flex-start;
    span {
      margin-bottom: 10px;
    }
  }
}
.buttons {
  margin-top: 20px;
  width: 50%;
  display: flex;
  justify-content: space-evenly;
}
</style>
