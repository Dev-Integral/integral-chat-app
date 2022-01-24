<template>
  <div class="chat-container">
    <LeftPanel />
    <MiddlePanel />
    <RightPanel />
  </div>
</template>

<script>
import LeftPanel from '../components/chatroom/LeftPanel';
import MiddlePanel from '../components/chatroom/MiddlePanel';
import RightPanel from '../components/chatroom/RightPanel';

export default {
  name: "Chat",
  components: {LeftPanel, MiddlePanel, RightPanel}
};
</script>

<style scoped>
.chat-container{
  display: grid;
  grid-template-columns:  1fr 3fr 1fr;
  gap: 30px;
  height: 92vh;
}
</style>
