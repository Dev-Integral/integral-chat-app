<template>
  <div class="middle-panel-container">
    <div v-if="friend" class="friend">
      <div
        class="messagefield"
        :class="{ 'friend-style': friend.id === messageObject.user.id }"
        v-for="(messageObject, index) in messagesArray"
        :key="index"
      >
        <div
          class="image-message"
          :class="{ 'friend-style-inner': friend.id === messageObject.user.id }"
        >
          <user-small-image :image="friend.image" :name="friend.name" />
          <div>
            <div
              :class="{
                'user-background': friend.id !== messageObject.user.id,
                'friend-background': friend.id === messageObject.user.id,
              }"
            >
              <p :id="`${messagesArray.length - 1 === index ? 'last' : index}`">
                {{ messageObject.message }}
              </p>
            </div>
            <span
              class="stamp-font"
              :class="{ 'stamp-style': friend.id === messageObject.user.id }"
              >{{ messageObject.timestamp }}</span
            >
          </div>
        </div>
      </div>
    </div>
    <div v-else>Select a chat</div>
    <InputField v-on:input="addMessage" />
  </div>
</template>

<script>
import UserSmallImage from "./UserSmallImage.vue";
import InputField from "./InputField";
import io from "socket.io-client";

export default {
  components: { UserSmallImage, InputField },
  name: "MiddlePanel",
  props: ["friend", "user"],
  data() {
    return {
      messagesArray: []
    };
  },
  methods: {
    addMessage(message) {
      this.messagesArray.push({
        message: message,
        user: {...this.user},
        timestamp: new Date(Date.now()).getHours(),
      });
      this.socketInstance.emit("message", {
        message: message,
        user: {...this.user},
        timestamp: new Date(Date.now()).getHours(),
      });
    },
  },
  mounted() {
    this.socketInstance = io("http://localhost:3000");
    this.socketInstance.on("message:broadcasted", (data)=> {
      this.messagesArray.push(data);
    })
  },
  updated() {
    document.getElementById("last")
      ? document.getElementById("last").scrollIntoView()
      : null;
  },
};
</script>

<style scoped>
p {
  font-family: cursive;
}

.middle-panel-container {
  background: #f3f6fb;
  border-radius: 15px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  height: 90vh;
  justify-content: space-between;
  position: relative;
  border: 1px solid #e0e1e4;
}
.friend {
  /* height: 80%; */
  overflow: scroll;
}
.image-message {
  display: flex;
  max-width: 70%;
  margin-bottom: 10px;
}
.friend-style {
  display: flex;
  flex-direction: column;
  align-items: flex-end;
}
.friend-style-inner {
  flex-direction: row-reverse;
}
.user-background {
  background: #fff;
  color: #525b72;
  padding: 15px;
  border-radius: 12px;
  margin-right: 10px;
  margin-bottom: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.05), 0 6px 20px 0 rgba(0, 0, 0, 0.005);
  font-size: 14px;
}
.friend-background {
  background: #1a233b;
  color: #fefefe;
  padding: 15px;
  border-radius: 12px;
  margin-right: 10px;
  margin-bottom: 10px;
  box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.05), 0 6px 20px 0 rgba(0, 0, 0, 0.005);
  font-size: 14px;
}
.stamp-font {
  font-size: 12px;
  color: #525c70;
}
.stamp-style {
  float: right;
  margin-right: 10px;
}
</style>