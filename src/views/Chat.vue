<template>
  <div class="chat-container">
    <LeftPanel v-on:converser="passConverser" />
    <MiddlePanel :friend="converser"/>
    <RightPanel />
  </div>
</template>

<script>
import LeftPanel from '../components/chatroom/LeftPanel';
import MiddlePanel from '../components/chatroom/MiddlePanel';
import RightPanel from '../components/chatroom/RightPanel';

export default {
  name: "Chat",
  components: {LeftPanel, MiddlePanel, RightPanel},
  data(){
    return{
      converser: null
    }
  },
  methods: {
    passConverser(e){
      console.log(e)
      this.converser = e;
    }
  }
};
</script>

<style scoped>
.chat-container{
  display: grid;
  grid-template-columns:  1fr 3fr 1fr;
  gap: 30px;
  height: 90vh;
}
</style>
