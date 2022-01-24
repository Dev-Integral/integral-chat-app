<template>
    <section class="section-three">
      <div class="title">
        <div class="grouped">
          <h4>{{convTitle}}</h4>
          <span class="indicator">{{ convList().length }}</span>
        </div>
        <p>></p>
      </div>
      <div class="content">
        <div
          class="item"
          v-for="(item, index) in convList()"
          :key="index"
          :class="{ 'active-conv': activeConv === index }"
          @click="setActiveConv(index)"
        >
          <div>
            <img :src="item.image" v-if="item.image" />
            <p v-else class="image-sub">{{ item.name[0] }} {{item.name.split(' ')[1][0]}}</p>
          </div>
          <div>{{ item.name }}</div>
        </div>
      </div>
    </section>
</template>

<script>
export default {
    name: 'ConversationList',
    props: ['convList', 'convTitle'],
    data() {
    return { activeConv: 0 };
  },
  methods: {
    setActiveConv(id) {
      this.activeConv = id;
    },
  },
}
</script>

<style scoped>
h2,
p {
  margin: 0px;
}
.section-three .title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.section-three .title .grouped {
  display: flex;
  align-items: center;
}
.section-three .indicator {
  background: #f3f6fb;
  padding: 5px 8px;
  border-radius: 50%;
  height: 100%;
  margin-left: 10px;
}
.section-three .content{
    overflow-y: scroll;
    height: 100px;
}
.section-three .content .item {
  display: flex;
  align-items: center;
  border-radius: 10px;
  padding: 5px 10px;
  cursor: pointer;
}
.section-three .content .item img, .image-sub {
  width: 50px;
  height: 50px;
  object-fit: cover;
  border-radius: 50%;
  margin-right: 15px;
  background: #f1f1f1;
  padding: 0;
  text-align: center;
  display: flex;
  justify-content: center;
  align-items: center;
  font-weight: bold;
}

.active-conv {
  background: #f3f6fb;
  margin: 5px 0;
  font-weight: bold;
  text-transform: capitalize;
}

</style>