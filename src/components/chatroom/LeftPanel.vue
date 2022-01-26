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
    <section class="section-three">
      <ConversationList
        :convList="convList"
        :convTitle="'Active Conversations'"
        v-on:selectedConverser="setConverser"
      />
    </section>
  </div>
</template>

<script>
import flash_logo from "../../assets/flash_logo.png";
import passport from "../../assets/passport.jpg";
import woman_logo from "../../assets/woman.png";

import ConversationList from "./ConversationList.vue";

export default {
  name: "LeftPanel",
  components: { ConversationList },
  emits: ['converser'],
  data() {
    return { flash_logo, passport, converser: null };
  },
  methods: {
    convList: () => [
      { image: passport, name: "Ayoola Taiwo", id: 1 },
      { image: flash_logo, name: "Benjamin Maradesa", id: 2 },
      { image: woman_logo, name: "Kelly Beauty", id: 3 },
      { image: "", name: "Boyega Amodu", id: 4 },
      { image: woman_logo, name: "Kelly Beauty", id: 5 },
      { image: passport, name: "Ayoola Taiwo", id: 6 },
      { image: flash_logo, name: "Benjamin Maradesa", id: 7 },
      { image: woman_logo, name: "Kelly Beauty", id: 8 },
      { image: "", name: "Boyega Amodu", id: 9 },
      { image: woman_logo, name: "Kelly Beauty", id: 10 },
    ],
    setConverser(data){
        this.converser = data;
        this.$emit('converser', data);
    }
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

.section-two {
  display: flex;
  align-items: center;
  justify-content: center;
  background: #f3f6fb;
  margin-top: 30px;
  margin-bottom: 30px;
  border-radius: 15px;
  padding: 20px;
  border: 1px solid #e0e1e4;
}
.section-two .content h2{
    margin-bottom: 10px ;
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
.section-three, .section-four{
    /* margin-bottom: 30px; */
}
</style>