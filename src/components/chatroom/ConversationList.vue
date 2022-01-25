<template>
    <section class="conv-list">
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
          @click="setActiveConv(index, item)"
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
  emits: ['selectedConverser'],
    props: ['convList', 'convTitle'],
    data() {
    return { activeConv: 0 };
  },
  methods: {
    setActiveConv(id, user) {
        this.$emit('selectedConverser', user)
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
.conv-list .title {
  display: flex;
  align-items: center;
  justify-content: space-between;
}
.conv-list .title .grouped {
  display: flex;
  align-items: center;
}
.conv-list .indicator {
  background: #f3f6fb;
  padding: 5px 8px;
  border-radius: 50%;
  height: 100%;
  margin-left: 10px;
}
.conv-list .content{
    overflow-y: scroll;
    height: 210px;
}
.conv-list .content .item {
  display: flex;
  align-items: center;
  border-radius: 10px;
  padding: 5px 10px;
  cursor: pointer;
}
.conv-list .content .item img, .image-sub {
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