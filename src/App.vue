<template>
  <SignUpForm />
</template>

<script>
import SignUpForm from './components/SignupForm.vue'

export default {
  name: 'App',
  components: { SignUpForm }
}

</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  margin-top: 60px;
}

body {
  font-family: 'Arial', sans-serif;
  background-color: #f4f4f4; /* Background color for the entire page */
  display: flex;
  justify-content: center;
  align-items: flex-start;
  height: 100vh;
}
</style>
