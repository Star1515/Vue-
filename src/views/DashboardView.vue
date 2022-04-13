<template>
  <div class="wrapper">
    <header>
      <div class="title">My personal costs</div>
      <div>My total {{ getFPV }}</div>
    </header>
    <main>
      <AddPaymentForm @addNewPayment="addData" ref="addpaymentForm" />
      <PaymentDisplay :list="currentElements" />
      <MyPagination
        :length="paymentsList.length"
        :n="n"
        :cur="cur"
        @changePage="onChangePage"
      />
    </main>
  </div>
</template>

<script>
import PaymentDisplay from "../components/PaymentDisplay.vue";
import AddPaymentForm from "../components/AddPaymentForm.vue";
import { mapMutations } from "vuex";
import MyPagination from "../components/MyPagination.vue";
export default {
  name: "App",
  components: {
    PaymentDisplay,
    AddPaymentForm,
    MyPagination,
  },
  data() {
    return {
      n: 5,
      cur: 1,
    };
  },
  computed: {
    // ...mapGetters(["getFullPaymentValue", "getPaymentsList"]),
    getFPV() {
      return this.$store.getters.getFullPaymentValue;
    },
    paymentsList() {
      return this.$store.getters.getPaymentsList;
    },
    currentElements() {
      return this.paymentsList.slice(
        this.n * (this.cur - 1),
        this.n * (this.cur - 1) + this.n
      );
    },
  },
  // actions: {
  //   ...mapActions(["fetchData"]),
  // },
  methods: {
    ...mapMutations({
      myMutation: "setPaymentListData",
    }),
    addData(data) {
      this.$store.commit("addDataPaymentsList", data);
    },
    onChangePage(p) {
      this.cur = p;
    },
  },
  created() {
    console.log(this.$store);
    // Global State
    // this.$store.commit('setPaymentListData', this.fetchData())
    // this.myMutation(this.fetchData())
    // this.$store.dispatch('fetchData')
  },
  async mounted() {
    await this.$store.dispatch("fetchData");
    this.cur = Number(this.$route.params.page);
  },
};
</script>