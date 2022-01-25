<template>
  <div class="item">
    <img :src="image" v-if="image" />
    <p v-else class="image-sub">
      {{ name[0] }} {{ name.split(" ")[1][0] }}
    </p>
  </div>
</template>

<script>
export default {
    name: 'UserSmallImage',
    props: ['image', 'name']
}
</script>

<style scoped>
.item img, .image-sub {
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

</style>