<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <hr />
    <!-- <button v-on:click="doThat('hello', $event)">Click me</button>
    <button @click="doThat('hello', $event)">Click me 2</button>
    <input type="text" @blur="onValidate" @input=""/> -->
    <div class="display">
      <input v-model.number="operand1" type="number" />
      <input v-model.number="operand2" type="number" />

      = {{ result }}
    </div>

    <!-- <input :value="operand1" @input="operand1 = $event.target.value"> -->
    <div class="keyboard">
      <button v-on:click="result = operand1 + operand2">+</button>
      <button @click="result = operand1 - operand2">-</button>
      <button @click="divide(operand1, operand2)">/</button>
      <button @click="multiply">*</button>
    </div>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  props: {
    msg: {
      type: String,
      default: "Empty Props",
    },
  },
  data() {
    return {
      message: "Hello Vue",
      operand1: 0,
      operand2: 0,
      result: 0,
    };
  },
  methods: {
    doThat(str, evnt) {
      console.log("click", str, evnt);
    },
    onValidate() {
      console.log("validation true");
    },
    divide(op1, op2) {
      this.result = op1 / op2;
    },
    multiply() {
      const { operand1, operand2 } = this;
      this.result = operand1 * operand2;
    },
  },
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