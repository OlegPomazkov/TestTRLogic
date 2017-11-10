<template>
  <div id="app">
    <h2> Накладная </h2>

    <table>
      <thead>
      	<tr>
      	  <th class="n">№</th>
    	  <th class="name">Наименование</th>
    	  <th class="amount">Количество</th>
    	  <th class="price">Цена</th>
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
    	  <td class="total name" colspan="3">ИТОГО</td>
    	  <td class="total price">{{totalSum}}</td>
    	</tr>
      </tfoot>
    </table>

  </div>
</template>
<!-- _________________________________________________________________________________________ -->
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
<!-- _________________________________________________________________________________________ -->
<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

table {
	margin-left: auto;
	margin-right: auto;
}

thead .n, 
thead .name, 
thead .amount, 
thead .price,
tfoot .total {
	background-color: #d5d5d5;
	color: #000;
}

tfoot .total.name {
	text-align: left;
	padding-left: 20px;
}

tbody .n, 
tbody .name, 
tbody .amount, 
tbody .price {
	background-color: #f5f5f5;
}

.n {
	width: 40px;
	text-align: center;
}

.name {
	width: 250px;
}

.amount {
	width: 100px;
	text-align: center;
}

.price {
	width: 100px;
	text-align: center;
}

.button {
	width: 100px;
}
</style>
