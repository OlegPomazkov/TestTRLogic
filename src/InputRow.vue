<template>
  <tr id="inputRow">
    <td class="not-used"></td>
    <td>
      <input v-model="name" placeholder="Введите наименование">
    </td>
    <td>
      <input v-model="amount" placeholder="Введите количество">      
    </td>
    <td>
      <input v-model="price" placeholder="Введите цену">
    </td>
    <td>
      <button v-on:click="addNewItem">Добавить</button>
    </td>    
  </tr>
</template>

<script>
export default {
  name: 'inputRow',
  data () {
    return {
      name: '',
      amount: '',
      price:''  
    }
  },
  methods:{
    addNewItem: function() {
      this.$emit('newItemAdded', {
        name: this.name, 
        amount: this.amount,
        price: this.price
      })
      this.name = '';
      this.amount = '';
      this.price = '';      
    }
  }  
}
</script>

<style>
#row {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

h1, h2 {
  font-weight: normal;
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
