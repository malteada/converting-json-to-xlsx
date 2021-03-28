<template>
  <div id="app">
    <h1>Testing json-as-xlsx</h1>
    <button @click="downloadFile">Download</button>
  </div>
</template>

<script>
import xlsx from 'json-as-xlsx'
export default {
  name: 'App',
  methods: {
    downloadFile: function () {
      var columns = [
        { label: 'User', value: 'user' },
        { label: 'Age', value: function x(row) { return (row.age + ' years') } },
        { label: 'Phone', value: function x(row) { return (row.more ? row.more.phone || '' : '') } }
      ]
      var content = [
        { user: 'Ana', age: 16, more: { phone: '11111111' } },
        { user: 'Luis', age: 19, more: { phone: '12345678' } }
      ]
      var settings = {
        sheetName: 'FirstSheet',
        fileName: 'MySpreadsheet'
      }
      xlsx(columns, content, settings)
    }
  }
}
</script>

<style>
#app {
  color: #2c3e50;
}
button {
  background-color: #008CBA;
  padding: 15px 32px;
  font-size: 16px;
  color: white;
}
</style>
