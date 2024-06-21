<template>
  <div class="card" :class="cardClasses">
    <img :src="user.Photo" class="card-img-top" alt="User Photo" />
    <div class="card-body">
      <div class="card-title">{{ user.Name }}</div>
      <div class="card-OrderNumber">{{ user.OrderNumber }}</div>
      <div class="card-text">{{ user.EmailId }}</div>
      <div class="card-text">{{ user.DispatchDate }}</div>
      <div v-if="user.AttentionRequired" class="card-text">
        <img
          src="@/assets/star-06-svgrepo-com.svg"
          alt="AttentionRequired"
          class="AttentionRequired"
        />
      </div>
    </div>
  </div>
</template>
<script >
export default {
  name: "Card",
  props: {
    user: Object,
  },
  computed: {
    cardClasses() {
      return {
        Confirmed: this.user.StatusOfOrder === "Confirmed",
        Running: this.user.StatusOfOrder === "Running",
        Future: this.user.StatusOfOrder === "Future",
        Major: this.user.TypeOfIssue === "Major",
        Minor: this.user.TypeOfIssue === "Minor",
      };
    },
  },
};
</script>
<style scoped>
.card {
  position: relative;
  width: 250px;
  background: #e9e1f1;
  height: 150px;
  overflow: visible;
  border-radius: 20px;
  color: #000;
  margin: 50px 0px;
}
.Confirmed {
  background: #8528db;
  color: #ffff;
}
.Running {
  background: #bd88ed;
  color: #ffff;
}
.Future {
  background: rgb(6, 75, 87);
  color: #ffff;
}
.Major {
  border: 5px solid red;
}
.Minor {
  border: 2px solid orangered;
}
.card-img-top {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -150%);
  width: 80px;
  height: 80px;
  border-radius: 50px;
}
.card-body {
  height: 75%;
  width: 90%;
  margin: auto;
  margin-top: 35px;
  text-align: center;
}
.AttentionRequired {
  position: absolute;
  top: -25px;
  left: 0%;
  width: 50px;
  height: 50px;
  border-radius: 50px;
}
.card-title {
  margin: 0;
  padding: 0;
  font-size: 30px;
  font-weight: 700;
}
.card-OrderNumber {
  font-size: 19px;
  font-weight: 700;
  margin-bottom: 10px;
}
.card-text {
  font-size: 19px;
}
</style>