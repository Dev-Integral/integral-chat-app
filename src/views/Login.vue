<template>
  <div class="signup-container">
    Integral chat app
    <div class="grouped-field">
      <div class="input-field">
        <input
          type="text"
          v-model="formData.username"
          placeholder="Enter your user name"
        />
      </div>
      <div class="input-field">
        <input
          type="text"
          v-model="formData.firstName"
          placeholder="Enter your first name"
        />
      </div>
    </div>
    <div class="grouped-field">
      <div class="input-field">
        <input
          type="text"
          v-model="formData.lastName"
          placeholder="Enter your last name"
        />
      </div>
      <div class="input-field">
        <input
          type="email"
          v-model="formData.emailAddress"
          placeholder="Enter your email"
        />
      </div>
    </div>
    <div class="input-field">
      <button @click="handleSubmit">Join</button>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  components: {},
  data () {
    return {
      formData: {
        username: '',
        firstName: '',
        lastName: '',
        emailAddress: '',
        // image: ''
      },
      error: {
        usernameError: false,
        firstNameError: false,
        lastNameError: false,
        emailAddressError: false,
        // imageError: false
      }
    }
  },
  methods: {
    handleSubmit () {
      const emailFormat = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      Object.keys(this.formData).forEach(field => {
        if (
          !this.formData[field] ||
          this.formData[field].length < 3 ||
          (field === 'emailAddress' && !emailFormat.test(this.formData[field]))
        ) {
          this.error[`${field}Error`] = true
        }
      });
    }
  }
}
</script>

<style scoped>
.signup-container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  position: fixed;
  width: 100%;
  height: 100%;
}
.grouped-field {
  display: flex;
  gap: 15px;
}
.input-field {
  border: 1px solid #333;
  border-radius: 30px;
  height: 40px;
  width: 200px;
  margin-bottom: 30px;
  padding: 5px;
  width: 200px;
}
.input-field input {
  height: 100%;
  width: 100%;
  outline: none;
  border: none;
  background: none;
  padding-left: 10px;
}
</style>
