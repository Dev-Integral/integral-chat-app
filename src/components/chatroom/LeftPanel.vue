<template>
  <div class="left-panel-container">
    <section class="section-one">
      <div class="content-one">
        <img v-bind:src="flash_logo" alt="flash" />
        <h1>FlashChat</h1>
      </div>
    </section>
    <section class="section-two">
      <div class="content">
        <img :src="passport" alt="user" />
        <div>
          <h2>Ayoola Taiwo</h2>
          <p>Software Engineer</p>
          Active
        </div>
      </div>
    </section>
    <ConversationList :convList="convList" :convTitle="'Active Conversations'" />
    <ConversationList :convList="convList" :convTitle="'Archived Conversations'" />

  </div>
</template>

<script>
import flash_logo from "../../assets/flash_logo.png";
import passport from "../../assets/passport.jpg";
import woman_logo from "../../assets/woman.png";

import ConversationList from "./ConversationList.vue";

export default {
  name: "LeftPanel",
  components: {ConversationList},
  data() {
    return { flash_logo, passport };
  },
  methods: {
    convList: () => [
      { image: passport, name: "Ayoola Taiwo" },
      { image: flash_logo, name: "Benjamin Maradesa" },
      { image: woman_logo, name: "Kelly Beauty" },
      { image: "", name: "Boyega Amodu" },
    ],
  },
};
</script>

<style scoped>
.section-one img {
  width: 30px;
  height: 35px;
  margin-right: 10px;
}
.section-one .content-one {
  display: flex;
  align-items: center;
}
.section-one .content-one h3 {
  margin: 0;
}

.section-two {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f3f6fb;
  margin-top: 30px;
  border-radius: 15px;
  padding: 20px;
  border: 1px solid #f3f3f3;
}
.section-two .content,
.section-two .content > div {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.section-two img {
  width: 100px;
  height: 100px;
  border-radius: 50%;
  margin-bottom: 15px;
  object-fit: cover;
}
.section-two h2,
.section-two p {
  margin-bottom: 10px;
}
</style>