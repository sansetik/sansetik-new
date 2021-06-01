<template>
  <div class="menu">
    <div class="logo">
      <nuxt-link to="/">sansetik</nuxt-link>
    </div>
    <div class="some_menu">
      <ul>
        <li><nuxt-link to="/">Главная</nuxt-link></li>
        <li><nuxt-link to="/blog">Блог</nuxt-link></li>
        <li><nuxt-link to="/portfolio">Портфолио</nuxt-link></li>
        <li><nuxt-link to="/services">Услуги</nuxt-link></li>
        <li><nuxt-link to="/about">О Сайте</nuxt-link></li>
      </ul>
    </div>
    <div class="login">
      <g-signin-button
        :params="googleSignInParams"
        @success="onSignInSuccess"
        @error="onSignInError">
        Sign in with Google
      </g-signin-button>
      <button ><span class="google_img"><img src="@/static/img/ant-design_google-circle-filled.svg" alt=""></span><span class="login_b">Вход</span> <span class="login_img"><img src="@/static/img/Arrow.svg" alt=""></span></button>
    </div>
  </div>
</template>

<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: "AppMenu",
  data () {
    return {
      /**
       * The Auth2 parameters, as seen on
       * https://developers.google.com/identity/sign-in/web/reference#gapiauth2initparams.
       * As the very least, a valid client_id must present.
       * @type {Object}
       */
      googleSignInParams: {
        client_id: '554535577319-jiqd47vmvoqpfv1dacg4vfm2qhqvef70.apps.googleusercontent.com'
      }
    }
  },
  methods: {
    onSignInSuccess (googleUser: { getBasicProfile: () => any }) {
      // `googleUser` is the GoogleUser object that represents the just-signed-in user.
      // See https://developers.google.com/identity/sign-in/web/reference#users
      const profile = googleUser.getBasicProfile() // etc etc
    },
    onSignInError (error: any) {
      // `error` contains any error occurred.
      console.log('OH NOES', error)
    }
  }
})

</script>

<style scoped>

.g-signin-button {
  /* This is where you control how the button looks. Be creative! */
  display: inline-block;
  padding: 4px 8px;
  border-radius: 3px;
  background-color: #3c82f7;
  color: #fff;
  box-shadow: 0 3px 0 #0f69ff;
}

.logo{
  margin-top: 20px;
}
.login{
  margin-top: 20px;
}
.google_img{
  margin-top: 6px;
  margin-left: 7px;
}
.login_b{
  margin-top: 7px;
  margin-left: 10px;
  margin-right: 10px;
  color: white;
  font-size: 14px;
  font-family: 'Roboto', sans-serif;
}
.login_img{
  margin-top: 8px;
  margin-right: 8px;
}
.login button{
  display: flex;
  justify-content: space-between;
  cursor: pointer;
  width: 111px;
  height: 34px;
  border-radius: 4px;
  border: none;
  background-color: #B77005;

}
.login button:hover{
  background-color: #d48106;
}
.logo a{
  font-family: 'Comfortaa', cursive;
  font-size: 36px;
  color: #024469;
  text-decoration: none;
}
.menu{

  height: 85px;

  border-bottom: solid 1px #E1E1E1;
  display: flex;
  justify-content: space-between;
  box-shadow: 0px 1px 2px rgba(0, 0, 0, 0.1);
}
.some_menu{
  margin-right: 100px;
  margin-top: 10px;
}
.some_menu ul li{
  margin-left: 20px;
  display: inline-block;
  text-decoration: none;
  list-style: none;
}
.some_menu ul li a{
  color: #024469;
  font-size: 18px;
  font-family: 'Roboto', sans-serif;
  text-decoration: none;
}
.some_menu ul li a:hover{
  border-bottom: dashed 1px #024469;
}
</style>
