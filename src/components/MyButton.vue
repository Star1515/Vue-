<template>
  <div>
    <slot name="append" v-bind="{ count: counter, text }" />
    <button @click="onClick"><slot>Clicked</slot> {{ counter }}</button>
  </div>
</template>

<script>
export default {
  name: "MyButton",
  props: {
    text: String,
  },
  data() {
    return {
      counter: 0,
    };
  },
  methods: {
    onClick() {
      this.counter++;
    },
    onMouseOver() {
      console.log("mouseover");
    },
  },
  beforeCreate() {
    console.log("beforeCreate");
  },
  created() {
    console.log("created");
  },
  beforeMount() {
    console.log("beforeMount");
  },
  mounted() {
    const btn = this.$el.querySelector("button");
    if (btn) {
      btn.addEventListener("mouseover", this.onMouseOver);
    }
    console.log("mounted");
  },
  beforeUpdate() {
    console.log("beforeUpdate");
  },
  updated() {
    console.log("updated");
  },
  beforeDestroy() {
    const btn = this.$el.querySelector("button");
    if (btn) {
      btn.removeEventListener("mouseover", this.onMouseOver);
    }
    console.log("beforeDestroy");
  },
  destroyed() {
    console.log("destroyed");
  },
};
</script>