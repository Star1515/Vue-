<template>
  <div id="app">
    <div class="wrapper">
      <header>
        <div class="title">My personal costs</div>
      </header>
      <main>
        <button @click="onPlay">Play me</button>
        <button @click="onStop">Stop</button>
        <video
          src="https://mdn.github.io/learning-area/javascript/apis/video-audio/finished/video/sintel-short.mp4"
          ref="player"
          controls
        />
        <AddPaymentForm @addNewPayment="addData" ref="addpaymentForm" />
        <PaymentDisplay :list="paymentsList" />
        <MyButton :list="myButton" />
      </main>
    </div>
  </div>
</template>

<script>
import PaymentDisplay from "./components/PaymentDisplay.vue";
import AddPaymentForm from "./components/AddPaymentForm.vue";
import MyButton from "./components/MyButton.vue";
export default {
  name: "App",
  components: {
    PaymentDisplay,
    AddPaymentForm,
    MyButton,
  },
  data() {
    return {
      paymentsList: [],
    };
  },
  methods: {
    onPlay() {
      this.$refs?.player?.play();
    },
    onStop() {
      this.$refs.player.pause();
    },
    fetchData() {
      return [
        {
          date: "28.03.2020",
          category: "Food",
          value: 169,
        },
        {
          date: "24.03.2020",
          category: "Transport",
          value: 360,
        },
        {
          date: "24.03.2020",
          category: "Food",
          value: 532,
        },
      ];
    },
    addData(data) {
      this.paymentsList.push(data);
    },
  },
  created() {
    this.paymentsList = this.fetchData();
  },
  mounted() {
    console.dir(this.$refs.player);
  },
};
</script>
<style lang='scss' scoped>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.title {
  font-size: 30px;
}
</style>