<template>
  <body>  
    <div class="calc">
      <div class="display">
        {{ current.length > 9 ? current.substring(0, 9) : current || 0}}
      </div>
      <div  @click="reset" class="btn percent">C</div>
      <div  class="btn percent">+/-</div>
      <div  @click="percent" class="btn percent">%</div>
      <div  @click="press('/')" class="btn operation">/</div>
      <div  @click="press('7')" class="btn">7</div>
      <div  @click="press('8')" class="btn">8</div>
      <div  @click="press('9')" class="btn">9</div>
      <div  @click="press('*')" class="btn operation">*</div>
      <div  @click="press('4')" class="btn">4</div>
      <div  @click="press('5')" class="btn">5</div>
      <div  @click="press('6')" class="btn">6</div>
      <div  @click="press('-')" class="btn operation">-</div>
      <div  @click="press('1')" class="btn">1</div>
      <div  @click="press('2')" class="btn">2</div>
      <div  @click="press('3')" class="btn">3</div>
      <div  @click="press('+')" class="btn operation">+</div>
      <div  @click="press('0')" class="btn null">0</div>
      <div  @click="dot" class="btn">.</div>
      <div  @click="result" class="btn operation">=</div>
    </div>
  </body>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      current: ''
    }
  },
  methods: {
    reset() {
      this.current = ''
    },
    press(number) {
      this.current = `${this.current}${number}`
    },
    dot() {
      if(!this.current.includes('.')) {
        this.current += '.';
      }
  },
    percent() {
      this.current = this.current/100*1
    },
    result() {
     this.current = eval(this.current)
    }
  }
}
</script>

<style>
body {
  background-color: rgba(222, 209, 219, 0.797);
}
.calc {
  text-align: center;
  width: 250px;
  margin-left: 200px;
  margin-top: 150px;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-auto-rows: minmax(50px, auto);
  font-size: 40px;
  cursor: pointer;
}
.display {
  grid-column: 1 / 5;
  background-color: #4f93e7;
}
.btn {
  border: 1px solid;
}
.btn:hover {
  border-radius: 10px;
}
.btn:active {
  background-color: blue;
}
.operation {
  background-color: rgb(237, 22, 22);
  color: antiquewhite ;
}
.operation:active {
  background-color: green;
}
.percent {
  background-color: rgb(186, 182, 182);
}
.null {
  grid-column: 1 / 3;
  text-align: left;
}
</style>
