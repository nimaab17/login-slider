<template>
  <div class="LogIn">
    <div class="LogIn__Form">
      <div class="LogIn__Form--title mb-4">
        <span> {{logInTitle}} </span>
      </div>
      <div class="LogIn__Form--inputs">
        <v-text-field v-model="form.userName" append-outer-icon="mdi-account" color="deep-purple accent-2" label="نام کاربری"
          placeholder="نام کاربری را وارد کنید ...." outlined></v-text-field>
        <v-text-field v-model="form.password" append-outer-icon="mdi-lock-outline" color="deep-purple accent-2"
          label="رمز عبور" placeholder="رمز عبور را وارد کنید ..." outlined></v-text-field>
        <v-text-field v-model="form.agentCode" append-outer-icon="mdi-face-agent" color="deep-purple accent-2"
          label="کد آژانس" placeholder="کد آژانس را وارد کنید..." outlined></v-text-field>
      </div>


      <v-btn class="btnStyle" :color="btnColor" block large @click="sendForm">
        <v-icon class="ml-3">mdi-send</v-icon> {{buttonTitle}}
      </v-btn>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        logInTitle: 'ورود',
        buttonTitle: "ورود",
        btnColor: "deep-purple accent-2",

        form: {
          userName: '',
          password: '',
          agentCode: '',
        }
      }
    },
    methods: {
      sendForm() {
        console.log(this.form);
      }
    }
  }

</script>

<style lang="scss" scoped>
  .LogIn {
    width: 100%;
    height: 100%;
    border-radius: 10px;
    background-color: rgba(255, 255, 255, 0.938);


    &__Form {
      height: 100%;
      width: 100%;
      padding: 30px;
      display: flex;
      flex-direction: column;
      align-items: center;
      justify-content: space-between;

      &--inputs {
        height: 100%;
        width: 100%;

      }

      &--title {
        color: black;
        font-size: 24px;
        font-weight: bold;
      }

      .btnStyle {
        color: white;
        font-size: 24px;
        font-weight: bold;
      }
    }
  }

</style>
