<template>
  <div class="block" @click="getTime" v-show="visible"></div>
</template>

<script>
export default {
  name: "GameBlock",
  props: {
    delay: Number,
  },
  data() {
    return {
      visible: false,
      timeCounter: null,
      timeTaken: 0,
    };
  },
  mounted() {
    //console.log("gameblock mounted: dealy time is : " + this.delay);
    setTimeout(() => {
      this.visible = true;
      //console.log("setting visible to true");
      this.timeCounter = setInterval(() => (this.timeTaken += 10), 10);
    }, this.delay);
  },
  methods: {
    getTime() {
      this.timeCounter = null;
      this.visible = false;
      console.log("emitting time taken : " + this.timeTaken);
      clearInterval(this.timeCounter);
      this.$emit("endgame", this.timeTaken);
    },
  },
};
</script>

<style>
.block {
  width: 60px;
  height: 60px;
  margin: 40px auto;
  padding: 52px;
  text-align: center;
  background-color: rgb(162, 0, 255);
  border: 5px;
  border-radius: 50%;
}
</style>
