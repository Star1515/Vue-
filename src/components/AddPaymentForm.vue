<template>
  <div>
    <input placeholder="Amount" v-model="value" />
    <input placeholder="Type" v-model="category" />
    <input placeholder="Date" v-model="date" />
    <button @click="onSave">Save!</button>
  </div>
</template>

<script>
export default {
  name: "AddPaymentForm",
  data() {
    return {
      value: "",
      category: "",
      date: "",
    };
  },
  computed: {
    getCurrentDate() {
      const today = new Date();
      const d = today.getDate();
      const m = today.getMonth() + 1;
      const y = today.getFullYear();
      return `${d}.${m}.${y}`;
    },
  },
  methods: {
    onSave() {
      const data = {
        value: this.value,
        category: this.category,
        date: this.data || this.getCurrentDate,
      };
      this.$emit("addNewPayment", data);
    },
  },
};
</script>

<style></style>