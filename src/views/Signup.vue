<template>
  <div class="signup-container">
    <h2 class="">Integral chat app</h2>
    <div class="grouped-field">
      <div class="input-field">
        <input
          type="text"
          v-model="formData.username"
          placeholder="Enter your user name"
          @change="validateInput"
          name="username"
        />
        <p v-if="error.usernameError" class="error-message">Invalid username</p>
      </div>
      <div class="input-field">
        <input
          type="text"
          v-model="formData.firstName"
          @change="validateInput"
          placeholder="Enter your first name"
          name="firstName"
        />
        <p v-if="error.firstNameError" class="error-message">
          Invalid first name
        </p>
      </div>
    </div>
    <div class="grouped-field">
      <div class="input-field">
        <input
          type="text"
          v-model="formData.lastName"
          @change="validateInput"
          placeholder="Enter your last name"
          name="lastName"
        />
        <p v-if="error.lastNameError" class="error-message">
          Invalid last name
        </p>
      </div>
      <div class="input-field">
        <input
          type="email"
          v-model="formData.emailAddress"
          placeholder="Enter your email"
          @change="validateInput"
          name="emailAddress"
        />
        <p v-if="error.emailAddressError" class="error-message">
          Invalid Email Address
        </p>
      </div>
    </div>
    <button @click="handleSubmit">Join</button>
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
        emailAddress: ''
        // image: ''
      },
      error: {
        usernameError: false,
        firstNameError: false,
        lastNameError: false,
        emailAddressError: false
        // imageError: false
      },
      validForm: false
    }
  },
  methods: {
    validateInput (e) {
      let inputName = e.target.name;
      const emailFormat = /^(([^<>()[\]\\.,;:\s@"]+(\.[^<>()[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/

      switch (inputName) {
        case 'username':
          !this.formData[inputName] || this.formData[inputName].length < 3?
          this.error[`${inputName}Error`] = true : this.error[`${inputName}Error`] = false;  
          break;
        case 'firstName':
          !this.formData[inputName] || this.formData[inputName].length < 3?
          this.error[`${inputName}Error`] = true : this.error[`${inputName}Error`] = false;  
          break;
        case 'lastName':
          !this.formData[inputName] || this.formData[inputName].length < 3?
          this.error[`${inputName}Error`] = true : this.error[`${inputName}Error`] = false;  
          break;
        case 'emailAddress':
          !emailFormat.test(this.formData[inputName]) ?
          this.error[`${inputName}Error`] = true : this.error[`${inputName}Error`] = false;
          break;
        default:
          break;
      }
    },
    handleSubmit () {
      let errorExist = [];
      Object.keys(this.error).find(field => {
        if(this.error[field]){
          errorExist.push(field);
        }
      })
      if(!errorExist.length) {
        alert('Fill the fields appropriately')
      }else{
        localStorage.setItem('chat-user-data', this.formData);
      }
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
.error-message {
  color: tomato;
  font-size: 12px;
  margin-top: 10px;
  margin-bottom: 15px;
  margin-left: 12px;
}
</style>
