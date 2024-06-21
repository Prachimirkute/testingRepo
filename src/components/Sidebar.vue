<template>
  <div class="sidebar">
    <div class="menu">
      <div v-for="item in menuItems" :key="item.id">
        <img :src="require(`@/assets/${item.icon}`)" alt="icon" class="icon" />
      </div>
    </div>
    <img :src="require(`@/assets/star.jpg`)" alt="icon" class="icon" />
  </div>
</template>
<script >
export default {
  name: "Sidebar",
  data() {
    return {
      menuItems: [
        { id: 1, icon: "star.jpg" },
        { id: 2, icon: "star.jpg" },
        { id: 3, icon: "star.jpg" },
      ],
    };
  },
};
</script>
<style scoped>
.sidebar {
  background-color: #333;
  width: 60px;
  height: 100vh;
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: space-between;
  padding-top: 20px;
}

.icon {
  width: 24px;
  height: 24px;
  margin-bottom: 20px;
  cursor: pointer;
}
</style>