<template>
  <div class="input-field">
    <input type="text" v-model="input" placeholder="Enter your message here" />
    <div class="submit-button" @click="handleSubmit">
      send <svg color='white' style="margin-left: 5px" viewBox="0 0 24 24" width="16" height="16" class="ekdr8vow dhq51u3o"><path fill="currentColor" d="M1.101 21.757 23.8 12.028 1.101 2.3l.011 7.912 13.623 1.816-13.623 1.817-.011 7.912z"></path></svg>
    </div>
  </div>
</template>

<script>
export default {
  name: "InputField",
  emits: ["input"],
  data() {
    return {
        input: ''
    };
  },
  methods:{
      handleSubmit(){
          this.$emit('input', this.input);
          this.input = '';
      }
  }
};
</script>

<style scoped>
.input-field {
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 8px;
  padding: 20px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.05), 0 6px 20px 0 rgba(0, 0, 0, 0.005);
  /* height: 20%; */
}
.input-field input {
  outline: none;
  width: 100%;
  height: 100%;
  border-radius: 5px;
  border: 1px solid #e0e1e4;
  padding: 3px 5px;
}
.submit-button {
  height: 100%;
  border: 1px solid;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px 10px;
  margin-left: 10px;
  border-radius: 8px;
  cursor: pointer;
  background: #004dfc;
  color: #fff;
}
</style>