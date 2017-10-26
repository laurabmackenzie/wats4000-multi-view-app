<template>
  <div class="home">
    <div class="form-container" v-show="showForm"><!--Modulates display of the .form-container-->
      <h1>Join the Web Developers Club!</h1>
      <p>Sign up to access our special, secret page. Just create an account and answer a brief survey.</p>

      <p class="error" v-show="showError">Some of the data has been entered incorrectly or is incomplete. Please try again</p><!--HTML element to display an error message for when the user submits invalid information. Uses v-show to show/hide this message based on the validity of the form data. -->

      <form v-on:submit.prevent="validateForm"><!--The validateForm method handles this form when it is submitted -->

        <fieldset>
        <legend>Account Information</legend>
        <p><label for="username">Username </label><input type="text" v-model="username" tabindex="0"></p><!--username field. -->

        <p><label for="email">Email </label><input type="email" v-model="email" tabindex="0"></p><!--email field. -->

        <p><label for="password">Password </label><input type="password" v-model="password" tabindex="0"></p><!--password field. -->

        <p><label for="passwordVerify">Verify Password </label><input type="password" v-model="passwordVerify" tabindex="0"></p><!--passwordVerify field. -->
        </fieldset>
        <p><input type="submit" value="Submit"></p>
      </form>
    </div>
    <div class="success-message" v-show="!showForm"><!--Modulates display of the .success-message using v-show and the showForm variable. -->
      <h1>Thank you for signing up!</h1>
      <p>Please take our new member survey. <router-link v-bind:to = "{name: 'Survey'}">Click Here</router-link></p>
<!-- TODO: Links to the survey page. -->
    </div>
  </div>
</template>

<script>
export default {
  name: 'Home',
  data () {
    return {
      username: '',
      email: '',
      password: '',
      passwordVerify: '',
      showForm: true,
      showError: false
    }
  },
  methods: {
    validateForm: function () {
      if ((this.username !="") && (this.email !="") && (this.password === this.passwordVerify)) {
        this.showForm=false;
      }
      else {
        this.showError=true;
      }
      // checks the following values:
      // username must not be blank
      // email must not be blank
      // password and passwordVerify must be equal
      // When the form is validated, shows the .success-message content
      // If the form is invalid, shows the form error message

    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.error {
  border: 1px solid #aa0000;
  padding: 1rem;
  color: #aa0000;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
