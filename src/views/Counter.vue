<template>
  <h1>{{ msg }}</h1>

  <div class="card">
    <ms-button type="primary" icon="fa-car" @click="count++">Number is: {{ count }}</ms-button>
  </div>

  <div class="example-table">
    <h2>Employee Table</h2>
    <MsTable
      :fields="fields"
      :rows="rows"
      @edit="handleEdit"
      @delete="handleDelete"
    />
  </div>
</template>

<script setup>
import { ref } from 'vue'
import MsTable from '@/components/ms-table/MsTable.vue'
import MsButton from '@/components/ms-button/MsButton.vue';

//#region Static Data
const fields = [
  { key: 'id', label: 'ID', type: 'number' },
  { key: 'name', label: 'Name', type: 'text' },
  { key: 'birthDate', label: 'Birth Date', type: 'date' },
  { key: 'amount', label: 'Amount ($)', type: 'number' }
]
//#endregion 

//#region State Data
const count = ref(0)
const rows = ref([
  {
    id: 1,
    name: 'John Doe',
    birthDate: '1990-01-15',
    amount: 1234.56
  },
  {
    id: 2,
    name: 'Jane Smith',
    birthDate: '1985-06-22',
    amount: 9876.54
  },
  {
    id: 3,
    name: 'Bob Johnson',
    birthDate: '1995-12-30',
    amount: 5432.10
  }
])
//#endregion

//#region Props
defineProps({
  msg: String,
})
//#endregion

//#region Methods
/**
 * Hàm xử lý sửa bản ghi
 * @param row 
 * createdby: pdthien - 15.10.2025
 */
const handleEdit = (row) => {
  console.log('Edit:', row)
}

/**
 * Hàm xử lý xóa bản ghi
 * @param row 
 * createdby: pdthien - 15.10.2025
 */
const handleDelete = (row) => {
  rows.value = rows.value.filter(item => item.id !== row.id)
}
//#endregion
</script>

<style scoped>
.example-table {
  margin: 2rem 0;
}
</style>
