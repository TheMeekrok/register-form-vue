<template>
  <section class="register">
    <h1>Регистрация</h1>
    <form @submit.prevent="sendData">
      <span>
        <img src="../assets/icons/user.svg">
        <input type="text" 
          id="username" 
          placeholder="Никнейм пользователя" 
          v-model.trim="username" 
          maxlength="32"/>
      </span>
      <span>
        <img src="../assets/icons/email.svg">
        <input type="text" 
          id="email" 
          placeholder="Почта" 
          v-model="watchEmail"
          maxlength="32"/>
      </span>
      <span>
        <img src="../assets/icons/password.svg">
        <input type="password" 
          id="password" 
          placeholder="Пароль" 
          v-model="watchPassword"
          maxlength="32"/>
      </span>
      <span>
        <img src="../assets/icons/password.svg">
        <input type="password" 
        id="password_repeat" 
        placeholder="Подтверждение пароля" 
        v-model="watchPasswordRepeat" 
        maxlength="32"/>
      </span>
      <div>
        <input type="submit" 
          value="Зарегистрироваться" 
          :disabled="emailHasError || passwordHasError || username == ''">
      </div>
    </form>
  </section>
</template>

<script>
export default {
  name: 'RegisterForm',
  data: () => {
    return {
      emailHasError: true, passwordHasError: true,
      username: '', watchEmail: '', watchPassword: '', watchPasswordRepeat: '',
    }
  },

  methods: { 
    sendData() {
      console.log({
        username: this.username, 
        email: this.watchEmail, 
        password: this.watchPassword 
      });
      this.username = this.watchEmail = this.watchPassword = this.watchPasswordRepeat = '';
    }
  },

  watch: {
    watchEmail: function(val) {
      if (val === 0 || !val.match(/^[a-zA-Z0-9-.]+@[a-zA-Z0-9-.]+(?:\.[a-zA-Z0-9-]+)*$/)) {
        this.emailHasError = true;
        return;
      }

      this.emailHasError = false;
    },

    watchPassword: function(val) {
      if (val.length < 8 || val.match(/[^a-zA-z0-9]/g) || val != this.watchPasswordRepeat) {
        this.passwordHasError = true;
        return;
      }

      this.passwordHasError = false;
    },

    watchPasswordRepeat: function(val) {
      if (val.length < 8 || val.match(/[^a-zA-z0-9]/g) || val != this.watchPassword) {
        this.passwordHasError = true;
        return;
      }

      this.passwordHasError = false;
    }
  }
}
</script>

<style scoped>
  section {
    display: flex;
    flex-direction: column;
    background-color: rgb(255, 239, 219);
    padding: 20px;
    border-radius: 10px;
    min-width: 400px;
    box-shadow: 10px 10px 10px rgb(205, 205, 205);
  }
  h1 {
    font-size: 24pt;
    margin-bottom: 20px;
    text-align: center;
  }
  div, span {
    margin-top: 30px; margin-bottom: 10px;
    margin-left: 10px; margin-right: 10px;
  }
  span {
    display: flex;
    align-items: center;
  }
  input[type=text], input[type=password] {
    border: 1px solid rgb(255, 255, 255);
    margin-left: 10px;
    border-radius: 3px;
    height: 25px; width: 100%;
    font-size: 12pt;
    transition: ease-in-out, height .35s ease-in-out;
    outline: none;
  }
  input[type=text]:focus, input[type=password]:focus {
    height: 40px;
  }
  input[type=submit] {
    font-size: 13pt; font-weight: bold; 
    border: 1px solid rgb(255, 255, 255);
    background-color: rgb(255, 190, 117);
    height: 50px; width: 100%;
    border-radius: 5px;
    transition: .3s;
  }
  input[type=submit]:hover {
    background-color: rgb(255, 208, 154);
  }
  img {
    height: 20px; width: 20px;
  }

</style>
