<template>
  <div class="calculator">
    <title>Calculator</title>
    <div id="app">
    <div class="grid">
      <input @keyup.enter="calc()" type="text" v-model="result" placeholder="0">
      <button @click="input(num)" class="cell num" v-for="(num, index) in numbers" :key="index">{{ num }}</button>
      <button @click="input(op)" class="cell op" v-for="(op, index) in operations" :key="index">{{ op }}</button>
      <button @click="reset()" class="cell op">R</button>
      <button @click="calc()" class="cell op">=</button>
    </div>
  </div>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      result: '',
      numbers: [1,2,3,4,5,6,7,8,9,0],
      operations: ['+','-','*','/'],
    }
  },
  methods: {
    input(char) {
      this.result = this.result.toString();
      this.result+=char;
    },
    reset() {
      this.result = '';
    },
    calc() {
      this.result = eval(this.result);
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
* {
  font-family: 'Gilroy',sans-serif;
  transition: 0.3s all;
    font-weight: 600;
}
#app {
  width: 200px;
  box-shadow: 0 3px 15px grey;
}
input[type="text"] {
  width: 180px;
  border: 0;
  color: #243849;
  font-size: 18px;
  padding: 5px 5px;
  text-align: right;
}
.grid {
  display: flex;                       
  flex-wrap: wrap;  
  justify-content: space-around;
  width: 100%;
  
}
.cell {
  flex: 33%;                       
  height: 50px;
  font-size: 18px;
  border: none;
}
.num {
  background-color: #243849;
  color: #fff;
  font-weight: 400;
}
.cell:hover{
  background-color: #182530;
}
.op {
  background-color: #ff9900;
  color: #243849;
}
</style>
