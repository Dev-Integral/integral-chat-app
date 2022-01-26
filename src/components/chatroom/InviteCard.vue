<template>
  <div class="invite-container">
    <h3>Invite Friends</h3>
    <p>Share invite link with friends and discuss all stuffs</p>
    <button>Copy Link</button>
  </div>
</template>

<style scoped>
.invite-container {
  display: flex;
  background: #f3f6fb;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;
  padding: 20px;
  border: 1px solid #e0e1e4;
  border-radius: 15px;
}
.invite-container h3 {
  margin-bottom: 15px;
}
.invite-container p {
  line-height: 20px;
  margin-bottom: 15px;
}
.invite-container button {
  background: #004dfc;
  border: none;
  color: #fff;
  padding: 15px;
  border-radius: 10px;
}
</style>