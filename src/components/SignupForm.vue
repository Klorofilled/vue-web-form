<template>
  <form @submit.prevent="handleSubmit">
    <label>Email</label>
    <input type="text" required v-model="email">

    <label>Password</label>
    <input type="password" required v-model="password">
    <div v-if="passwordError" class="error">{{ passwordError }}</div>

    <label>Role:</label>
    <select v-model="role">
        <option value="developer">Web Dev</option>
        <option value="designer">Web Des</option>
    </select>

    <label >Skills:</label>
    <input type="text" v-model="tempSkill" @keyup.alt="addSkill">
    <div v-for="skill in skills" :key="skill" class="pill" @click="deleteSkill(skill)">
      {{ skill }}
    </div>

    <div class="terms">
      <input type="checkbox" required v-model="terms">
      <label class="checkbox-label">Accept Terms & Conditions</label>
    </div>

    <div class="submit">
      <button>Create an Account</button>
    </div>

  </form>
  
  
</template>

<script>
export default {
    data() {
        return {
            email: '',
            password: '',
            role: '',
            terms: false,
            tempSkill: '',
            skills: [],
            passwordError: null,
        }
    },
    methods: {
      addSkill(e) {
        if (e.key === ',' && this.tempSkill) {
          if (!this.skills.includes(this.tempSkill)) {
            this.skills.push(this.tempSkill)
          }
          this.tempSkill = ''
        }
      },
      deleteSkill(skill) {
        // delete this.skills[this.skills.indexOf(skill)]
        this.skills = this.skills.filter((item) => {
          return skill !== item
        })
      },
      handleSubmit() {
        // validate password
      this.passwordError = this.password.length > 5 ?
        '' : 'Password must be at least 6 characters long'

      if (!this.passwordError) {
        // make request to database to save user
        console.log('email: ', this.email)
        console.log('password: ', this.password)
        console.log('role: ', this.role)
        console.log('skills: ', this.skills)
        console.log('terms accepted: ', this.terms)
      }
    }
  }
}
</script>

<style>
form {
  background-color: #ffffff;
  box-shadow: 0 0 10px rgba(0, 0, 0, 0.1);
  border-radius: 8px;
  padding: 50px;
  width: 500px;
}

label {
  display: block;
  font-size: 14px;
  margin-bottom: 8px;
  color: #333333;
}

input, select {
  width: 100%;
  padding: 10px;
  margin-bottom: 16px;
  border: 1px solid #dddddd;
  border-radius: 4px;
  box-sizing: border-box;
}

div.terms {
  padding: 20px;
}

input[type="checkbox"] {
  display: inline-block;
  width: 16px;
  margin-right: 8px;
  position: relative;
  top: 2px;
}

label.checkbox-label {
  display: inline-block;
  align-items: center;
  font-size: 14px;
  color: #333333; /* Label text color */
  margin-bottom: 16px;
}

div.pill {
  display: inline-block;
  margin-right: 8px;
  padding: 8px 16px;
  border-radius: 20px; /* Adjust the border-radius to control the pill shape */
  background-color: #008080; /* Teal color for the pill background */
  color: #ffffff; /* Text color for the pill */
  font-size: 12px;
  font-weight: bold;
  text-align: center;
}

button {
  background: slategray;
  border: 0;
  padding: 10px 20px;
  margin-top: 20 px;
  color: white;
  border-radius: 20px;
}

.submit {
  text-align: center;
}

.error {
    color: darkred;
    margin-bottom: 10px;
    font-size: 0.8em;
    font-weight: bold;
  }
</style>