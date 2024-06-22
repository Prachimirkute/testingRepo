<template>
  <div class="Home">
    <Sidebar />
    <div :style="{ 'margin-left': sidebarWidth }" class="mainContent">
      <div class="Title">Online Ordering Platform</div>
      <div class="Labels">
        <div class="label">
          <div class="box"></div>
          <div class="text">Confirmed Order</div>
        </div>
        <div class="label">
          <div class="box"></div>
          <div class="text">Running Order</div>
        </div>
        <div class="label">
          <div class="box"></div>
          <div class="text">New Order</div>
        </div>
        <div class="label">
          <div class="box"></div>
          <div class="text">Future Order</div>
        </div>
        <div class="label">
          <div class="box">
            <img
              src="@/assets/star-06-svgrepo-com.svg"
              alt="AttentionRequired"
              class="box"
            />
          </div>
          <div class="text">Attention Required</div>
        </div>
        <div class="label">
          <div class="box"></div>
          <div class="text">Minor Issue</div>
        </div>
        <div class="label">
          <div class="box"></div>
          <div class="text">Major Issue</div>
        </div>
      </div>
      <div class="filtercontainer">
        <img
          src="@/assets/filter-svgrepo-com.svg"
          alt="AttentionRequired"
          class="Filter"
        />
      </div>
      <div class="user-list">
        <Card v-for="user in users" :key="user.id" :user="user" />
      </div>
    </div>
  </div>
</template>

<script >
import Card from "./Card.vue";
import Sidebar from "./Sidebar.vue";
import userData from "@/db.json";
import { sidebarWidth } from "./State";
import axios from "axios";
export default {
  name: "Home",
  components: {
    Sidebar,
    Card,
  },
  setup() {
    return { sidebarWidth };
  },
  data() {
    return {
      users: [],
    };
  },
  mounted() {
    this.fetchProducts();
  },
  methods: {
    async fetchProducts() {
      try {
        const response = await axios.get("http://localhost:3000/users");
        console.log(response.data);
        this.users = response.data;
      } catch (error) {
        console.error("Error fetching products:", error);
      }
    },
  },
};
</script>
<style scoped>
.Home {
  display: flex;
}
.Home::-webkit-scrollbar {
  display: none;
}
.mainContent {
  width: calc(100vw - 60px);
}
.mainContent::-webkit-scrollbar {
  display: none;
}
.Title {
  width: 80%;
  height: 100px;
  background-color: #3f0b6f;
  margin: auto;
  display: flex;
  align-items: center;
  justify-content: center;
  color: white;
  font-size: 60px;
  font-weight: 700;
  border-radius: 20px;
  margin-top: 20px;
}
.Labels {
  width: 75%;
  height: 100px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  align-items: center;
  justify-content: center;
  margin: 20px auto;
}
.label {
  width: 200px;
  display: flex;
  justify-content: center;
  align-items: center;
  gap: 30px;
  margin: auto;
}
.box {
  width: 30px;
  height: 30px;
  border-radius: 10px;
}
.label:nth-child(1) > .box {
  background-color: #8528db;
}
.label:nth-child(2) > .box {
  background-color: #bd88ed;
}
.label:nth-child(3) > .box {
  background-color: #e9e1f1;
}
.label:nth-child(4) > .box {
  background-color: rgb(6, 75, 87);
}
.label:nth-child(6) > .box {
  outline-offset: -5px;
  outline: 2px solid orangered;
}
.label:nth-child(7) > .box {
  outline-offset: -5px;
  outline: 4px solid red;
}
.text {
  width: 130px;
}
.filtercontainer {
  width: 100%;
}
.Filter {
  width: 50px;
  height: 50px;
  margin-left: 93%;
}
.user-list {
  display: grid;
  justify-items: center;
  align-items: center;
  grid-template-columns: repeat(4, 1fr);
}
</style>