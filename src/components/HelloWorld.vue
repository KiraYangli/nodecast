<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click="checklista">get list!</button>
    <ul>
      <li v-for="item in lista">
        {{ item.name }}=={{ item.age }}
      </li>
    </ul>
  </div>
</template>

<script>
import axios from 'axios';
export default {
  name: 'HelloWorld',
  data () {
    return {
      msg: 'Welcome!',
      lista:[
        {"name":"zhangsan","age":20},
        {"name":"lisi","age":30},
        {"name":"wangsir","age":40}]
    }
  },
  methods: {
    checklista(){
      axios.get('/lista')
      .then(res =>{
        res.data.forEach((ele)=>{
          this.lista.push(ele);
        });
        // this.lista = Array.concat(this.lista,res.data);
      })
      .catch(err => {
        console.log(err);
      })
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  /*display: inline-block;*/
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
