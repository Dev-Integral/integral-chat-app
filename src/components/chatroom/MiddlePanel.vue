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
    <InputField v-on:input="populateInput" />
  </div>
</template>

<script>
import UserSmallImage from "./UserSmallImage.vue";
import InputField from "./InputField";

export default {
  components: { UserSmallImage, InputField },
  name: "MiddlePanel",
  props: ["friend", "user"],
  data() {
    return {
      messagesArray: [
        {
          user: { id: 1, image: "", name: "Ayoola Taiwo" },
          message:
            "hello Bill, trust you doing greatsdljndjd, sweowe wwkedoid ewdoewoidew ewoideowiewje nowedoewnwe3do3 o32w3rdnoawlwoe dweoidoweid eowdweoewe",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
        {
          user: { id: 2, image: "", name: "Bill Gate" },
          message: "hi henry, I'm fine fdl fdd reoker kerpk",
          timestamp: "9h ago",
        },
      ],
    };
  },
  methods:{
    populateInput(data){
      this.messagesArray.push({
        message: data,
        user: this.user,
        timestamp: new Date(Date.now()).getHours()
        });
    }
  },
  updated() {
    document.getElementById("last") ? document.getElementById("last").scrollIntoView() : null;
  },
};
</script>

<style scoped>
.middle-panel-container {
  background: #f3f6fb;
  border-radius: 15px;
  padding: 20px;
  display: flex;
  flex-direction: column;
  height: 90vh;
  justify-content: space-between;
  position: relative;
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