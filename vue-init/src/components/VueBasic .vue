<template>
  <div>
    {{msg}}
    <input :type="type" @click="clickEvent" v-model='inputValue'/>
    <ul>
      <!-- :style='[itemColor]'数组语法：:style=itemColor
      :class="[{background:isactive}]"对象语法：:class='{backgound:isactice}'-->
      <li
        :class="[{background:isactive}]"
        v-for="(item,index) in items"
        :key="index"
        :style="[itemColor]"
        @click="isactive = !isactive"
      >{{item}}</li>
    </ul>
    <p>Original message: "{{ message }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
    <p>Computed reversed message: "{{ reversedMessage }}"</p>
  </div>
</template>

<script>
export default {
  name: "HelloWorld",
  data() {
    return {
      msg: "Welcome to Your Vue.js App",
      type: "text",
      items: ["item1", "item2", "item3", "item4"],
      isactive: true,
      background: "background",
      itemColor: {
        color: "green",
      },
      message: "Hello",
      inputValue:'hello'
      // itemClass:{
      //   'background' : this.isactive
      // }
    };
  },
  methods: {
    //函数的三种写法
    // clickEvent:()=>{
    //   console.log(1)
    // }
    // clickEvent(){
    //   console.log(1)
    // },
    clickEvent: function () {
      console.log(this);
      console.log("clickevent...");
      console.log(1);
    },
    getItemClass() {
      //注意这里不要写成箭头函数，有this指向的问题
      return { background: this.isactive };
    },
  },
  watch:{
    inputValue(newValue,oldValue){
      console.log(newValue+' '+oldValue);
    }
  },
  computed: {
    // 计算属性的 getter
    reversedMessage: function () {
      // `this` 指向 vm 实例
      console.log('触发计算属性');
      return this.message.split("").reverse().join("");
    },
  },
  beforeCreate() {
    console.log("beforeCreate..." + this.isactive);
  },
  created() {
    console.log(this);
    console.log("Created..." + this.isactive);
  },
  beforeMount() {
    console.log("beforeMouted..." + this.isactive);
  },
  mounted() {
    console.log("mouted..." + this.isactive);
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.background {
  background-color: pink;
}
</style>
