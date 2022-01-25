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
              <p>{{ messageObject.message }}</p>
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
    <div class="input-field">
      <input type="text" placeholder="Enter your message here" />
      <div class="submit-button" @click="handleSubmit">send</div>
    </div>
  </div>
</template>

<script>
import UserSmallImage from "./UserSmallImage.vue";
export default {
  components: { UserSmallImage },
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
      ],
    };
  },
  methods: {},
};
</script>

<style scoped>
.middle-panel-container {
  background: #f3f6fb;
  border-radius: 15px;
  padding: 20px ;
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  position: relative;
}
.image-message {
  display: flex;
  max-width: 70%;
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
  color: #525c72;
  padding: 15px;
  border-radius: 12px;
  margin-right: 10px;
  margin-bottom: 10px;
}
.friend-background {
  background: #1a233b;
  color: #fefefe;
  padding: 15px;
  border-radius: 12px;
  margin-right: 10px;
  margin-bottom: 10px;
}
.stamp-font {
  font-size: 14px;
  color: #525c70;
}
.stamp-style {
  float: right;
  margin-right: 10px;
}
.input-field {
  display: flex;
  align-items: center;
  justify-content: center;
  background: white;
  border-radius: 8px;
  padding: 20px;

}
.input-field input{
  outline: none;
  width: 100%;
  height: 100%;
  border-radius: 5px;
  border: 1px solid;
  padding: 3px 5px;
}
.submit-button{
  height: 100%;
  border: 1px solid;
  display: flex;
  align-items: center;
  justify-content: center;
  padding: 4px 10px;
  margin-left: 10px;
  border-radius: 8px;
  cursor: pointer;
}
</style>