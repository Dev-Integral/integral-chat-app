<template>
  <div class="chat-container">
    <LeftPanel v-on:converser="passConverser" />
    <MiddlePanel :friend="converser" :user="user" />
    <RightPanel />
  </div>
</template>

<script>
import LeftPanel from "../components/chatroom/LeftPanel";
import MiddlePanel from "../components/chatroom/MiddlePanel";
import RightPanel from "../components/chatroom/RightPanel";

// import flash_logo from "../../assets/flash_logo.png";
import passport from "../assets/passport.jpg";
// import woman_logo from "../../assets/woman.png";


export default {
  name: "Chat",
  components: { LeftPanel, MiddlePanel, RightPanel },
  data() {
    return {
      converser: null,
      user: { image: passport, name: "Ayoola Taiwo", id: 1 }
    };
  },
  methods: {
    passConverser(e) {
      this.converser = e;
    },
  },
};
</script>

<style scoped>
.chat-container {
  display: grid;
  grid-template-columns: 1fr 3fr 1fr;
  gap: 30px;
  height: 90vh;
}
</style>
