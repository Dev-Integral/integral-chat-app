<template>
  <div class="signup-container">
    Integral chat app
    <div class="grouped-field">
      <div class="input-field">
        <input
          type="text"
          v-model="username"
          placeholder="Enter your user name"
        />
      </div>
      <div class="input-field">
        <input
          type="text"
          v-model="firstName"
          placeholder="Enter your first name"
        />
      </div>
    </div>
    <div class="grouped-field">
    <div class="input-field">
      <input
        type="text"
        v-model="lastName"
        placeholder="Enter your last name"
      />
    </div>
    <div class="input-field">
      <input
        type="text"
        v-model="emailAddress"
        placeholder="Enter your email"
      />
    </div>
    </div>
    <div class="input-field">
      <input type="text" v-model="image" placeholder="Enter your image" />
    </div>
  </div>
</template>

<script>
export default {
  name: 'Login',
  components: {},
  data () {
    return {
      username: '',
      firstName: '',
      lastName: '',
      emailAddress: '',
      image: ''
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
.grouped-field{
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
