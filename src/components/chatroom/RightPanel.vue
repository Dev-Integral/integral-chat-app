<template>
  <div class="right-panel-container">
    <FriendInfoCard />
    <inviteCard />
  </div>
</template>

<script>
import FriendInfoCard from "./FriendInfoCard.vue";
import InviteCard from "./InviteCard";
export default {
  name: "RightPanel",
  components: { FriendInfoCard, InviteCard },
};
</script>

<style scoped>
.right-panel-container {
  /* border-radius: 15px; */
  display: flex;
  flex-direction: column;
  justify-content: space-between;
}
</style>