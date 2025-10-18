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
    >
      <template #Name="{ row, value }">
        <div style="display: flex; flex-direction: column;">
          <strong>{{ value }}</strong>
          <div v-if="row.IsUser" style="color: green;"><i class="fa fa-user"></i> Nhân viên</div>
        </div>
      </template>
    </MsTable>
  </div>
</template>

<script setup>
import { ref } from 'vue'
import MsTable from '@/components/ms-table/MsTable.vue'
import MsButton from '@/components/ms-button/MsButton.vue';

//#region Static Data
const fields = [
  { key: 'Id', label: 'ID', type: 'number' },
  { key: 'Name', label: 'Họ và tên', type: 'custom' },
  { key: 'BirthDate', label: 'Ngày sinh', type: 'date' },
  { key: 'Amount', label: 'Thực lĩnh ($)', type: 'number' }
]
//#endregion 

//#region State Data
const count = ref(0)
const rows = ref([
  {
    Id: 1,
    Name: 'John Doe',
    BirthDate: '1990-01-15',
    Amount: 1234.56,
    IsUser: true
  },
  {
    Id: 2,
    Name: 'Jane Smith',
    BirthDate: '1985-06-22',
    Amount: 9876.54,
    IsUser: false
  },
  {
    Id: 3,
    Name: 'Bob Johnson',
    BirthDate: '1995-12-30',
    Amount: 5432.10,
    IsUser: true
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
  rows.value = rows.value.filter(item => item.Id !== row.Id)
}
//#endregion
</script>

<style scoped>
.example-table {
  margin: 2rem 0;
}
</style>
