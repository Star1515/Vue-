   </div>

    <div v-show="checked">
      <button v-for="btn in btns" :key="btn">
      <button v-for="btn in btns" :key="btn" @click="pushBtn(btn)">
        {{ btn }}
      </button>
      <button @click="sliceOperand()">&#10229;</button>
    </div>

    <div>

        <input
          type="radio"
          id="one"

          name="operand"
          v-model="operand1"
          @click="selectOperand1()"
          v-model="picked"
          value="operand1"
        />
        <label for="one">Операнд 1</label>

        <input
          type="radio"
          id="two"

          name="operand"
          v-model="operand2"
          @click="selectOperand2()"
          v-model="picked"
          value="operand2"
        />
        <label for="two">Операнд 2</label>

@@ -68,23 +67,29 @@ export default {
    return {
      message: "Hello Vue",
      operands: ["+", "-", "*", "/", "**", "//"],
      btns: [0, "1", "2", "3", "4", "5", "6", "7", "8", "9", "<--"],
      btns: [0, "1", "2", "3", "4", "5", "6", "7", "8", "9"],
      operand1: "",
      operand2: "",
      result: 0,
      checked: "",
      selectOp1: false,
      selectOp2: false,
      picked:''
    };
  },
  methods: {
    selectOperand1(){
      this.selectOp1 = true
      this.selectOp2 = false
    sliceOperand(){
      if(this.picked === 'operand1'){
        this.operand1 = Number(String(this.operand1).slice(0,-1))
      }else if(this.picked === 'operand2'){
        this.operand2 = Number(String(this.operand2).slice(0,-1))
      }
    },
    selectOperand2(){
      this.selectOp1 = false
      this.selectOp2 = true
    pushBtn(btn) {
      if(this.picked === 'operand1'){
        this.operand1 = +(this.operand1 + btn)
      }else if(this.picked === 'operand2'){
        this.operand2 = +(this.operand2 + btn)
      }
       
    },
    doThat() {
      console.log("счелк");