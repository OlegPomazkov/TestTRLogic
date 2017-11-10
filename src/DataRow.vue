<template>
  <tr>
    <td>
       {{indexData + 1}}
    </td>
    <td>
      <input v-model="nameData" placeholder="Введите наименование" @change="renewRowData">
    </td>
    <td>
      <input v-model="amountData" placeholder="Введите количество" @change="renewRowData">      
    </td>
    <td>
      <input v-model="priceData" placeholder="Введите цену" @change="renewRowData">
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
    },
    renewRowData: function(e) {
      var newDataObj = {
        index: this.indexData,
        name:this.nameData,
        amount: this.amountData,
        price: this.priceData
      } 
      this.$emit('rowDataChanged', newDataObj)
    }
  }  
}
</script>

<style>
tr {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
