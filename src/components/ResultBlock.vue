<template>
  <div class="hello">
    <h1>{{ result }}</h1>
  </div>
</template>

<script>
export default {
  name: "ResultBlock",
  props: {
    time: Number,
  },
  data() {
    return {
      result: null,
    };
  },
  mounted() {
    console.log("in mounted of resultBlock");
    if (this.time < 250) {
      this.result = "Wow! You have lightening reflexes!!!";
    } else if (this.time < 500) {
      this.result = "Yay! You have Cheetah reflexes!";
    } else if (this.time < 750) {
      this.result = "You are as slow as a tortoise, better luck next time";
    } else {
      this.result = "You are slower than a sloth, better luck next time!";
    }
  },
  methods: {},
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
