<template>
  <div id="app">
    <h2> Накладная </h2>

    <table>
      <thead>
      	<tr>
      	  <th>№</th>
    	  <th>Наименование</th>
    	  <th>Количество</th>
    	  <th>Цена</th>
    	</tr>
      </thead>
      <tbody> 
        <data-row 
          v-for="rowData in rowsData" 
          :rowData="rowData"
          v-on:rowDataChanged="rowDataChanged"
          v-on:deleteItem="deleteItem">
        </data-row>
      </tbody>
      <tfoot>
       	<input-row v-on:newItemAdded="addNewItem"></input-row>
        <tr>
    	  <td colspan="3">ИТОГО</td>
    	  <td>{{totalSum}}</td>
    	</tr>
      </tfoot>
    </table>

  </div>
</template>

<script>

import inputRow from './InputRow.vue'
import dataRow from './DataRow.vue'

export default {	 
  name: 'app',
  components: {
    'data-row': dataRow,
    'input-row': inputRow
  },

  data () {
    return {
      rowsData: []
    }
  },

  computed: {
    totalSum: function () {
      var sum = 0
      this.rowsData.forEach((item)=>{sum += (+item.price)*(+item.amount)} )
      return sum
    }
  },

  methods: {
    addNewItem: function (obj) {
      obj.index = this.rowsData.length	
      this.rowsData.push(obj)
    },
    rowDataChanged: function (dataObj) {	
      this.rowsData.splice((+dataObj.index), 1, dataObj)     
    },
    deleteItem: function (index) {	
      this.rowsData.splice(index, 1)
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

</style>
