<template>
  <tr>
    <td>
       {{indexData + 1}}
    </td>
    <td>
      <input v-model="nameData" placeholder="Введите наименование">
    </td>
    <td>
      <input v-model="amountData" placeholder="Введите количество">      
    </td>
    <td>
      <input v-model="priceData" placeholder="Введите цену">
    </td>
    <td>
      <button v-on:click="deleteItem">Удалить</button>
    </td>    
  </tr>
</template>

<script>
export default {
  name: 'dataRow',
  props: {
    rowData: Object
},

  data () {

    return {
      indexData: +this.rowData.index,
      nameData: this.rowData.name,
      amountData: +this.rowData.amount,
      priceData: +this.rowData.price
    }
  },  

  methods:{
    deleteItem: function() {
      this.$emit('deleteItem', +this.indexData)
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
