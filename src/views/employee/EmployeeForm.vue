<template>
  <transition name="modal-fade">
    <div class="modal-overlay" @click.self="closeForm">
      <div class="modal-content">
        <div class="modal-header">
          <h3>{{ formTitle }}</h3>
          <ms-button class="close-btn" icon="fa-times" @click="closeForm" />
        </div>
        
        <div class="modal-body">
          <div class="form-row">
            <div class="form-group">
              <label for="name" class="required">Họ và tên</label>
              <input 
                type="text" 
                id="name" 
                v-model="formData.Name" 
                class="form-control"
                placeholder="Nhập họ và tên"
                autocomplete="name"
              />
            </div>
          </div>

          <div class="form-row">
            <div class="form-group">
              <label for="dob">Ngày sinh</label>
              <input 
                type="date" 
                id="dob" 
                v-model="formData.BirthDate" 
                class="form-control"
              />
            </div>
            
            <div class="form-group">
              <label for="amount">Thực lĩnh</label>
              <input 
                type="number" 
                id="amount" 
                v-model="formData.Amount" 
                class="form-control"
                placeholder="0"
                min="0"
                step="1000"
              />
            </div>
          </div>

          <div class="form-row">
            <div class="form-group checkbox-group">
              <label class="checkbox-label">
                <input type="checkbox" v-model="formData.IsUser" class="checkbox-input" />
                <span class="checkbox-text">Là nhân viên</span>
              </label>
            </div>
          </div>
        </div>
        
        <div class="modal-footer">
          <ms-button type="secondary" icon="fa-times" @click="closeForm">
            Hủy
          </ms-button>
          <ms-button type="primary" icon="fa-save" @click="saveForm">
            Lưu
          </ms-button>
        </div>
      </div>
    </div>
  </transition>
</template>

<script setup>
import { ref, watch, computed } from 'vue';
import MsButton from '@/components/ms-button/MsButton.vue';
import { EmployeeModel } from '@/models/employeeModel.js';

const props = defineProps({
  modelValue: {
    type: Boolean,
    default: false
  },
  employee: {
    type: Object,
    default: () => ({})
  }
});

const emit = defineEmits(['update:modelValue', 'save']);

const formData = ref(new EmployeeModel());

// Computed property cho tiêu đề form
const formTitle = computed(() => {
  return formData.value.Id 
    ? 'Sửa thông tin nhân viên' 
    : 'Thêm mới nhân viên';
});

// Watch employee prop để cập nhật form data
watch(() => props.employee, (newVal) => {
  formData.value = new EmployeeModel(newVal);
}, { immediate: true, deep: true });

const closeForm = () => {
  emit('update:modelValue', false);
};

const saveForm = () => {
  emit('save', formData.value);
  closeForm();
};
</script>

<style scoped>
/* Modal Transitions */
.modal-fade-enter-active,
.modal-fade-leave-active {
  transition: opacity 0.3s ease;
}

.modal-fade-enter-active .modal-content,
.modal-fade-leave-active .modal-content {
  transition: transform 0.3s ease;
}

.modal-fade-enter-from,
.modal-fade-leave-to {
  opacity: 0;
}

.modal-fade-enter-from .modal-content,
.modal-fade-leave-to .modal-content {
  transform: scale(0.9) translateY(-20px);
}

/* Modal Overlay */
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  bottom: 0;
  background-color: rgba(0, 0, 0, 0.6);
  display: flex;
  justify-content: center;
  align-items: center;
  z-index: 1000;
  padding: 20px;
  backdrop-filter: blur(2px);
}

/* Modal Content */
.modal-content {
  background-color: white;
  border-radius: 12px;
  width: 600px;
  max-width: 100%;
  max-height: 90vh;
  overflow-y: auto;
  box-shadow: 0 10px 40px rgba(0, 0, 0, 0.2);
  display: flex;
  flex-direction: column;
}

/* Modal Header */
.modal-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 24px 24px 16px;
  border-bottom: 1px solid #e5e7eb;
}

.modal-header h3 {
  margin: 0;
  font-size: 1.5rem;
  font-weight: 600;
  color: #1f2937;
}

.close-btn {
  background: none;
  border: none;
  font-size: 1.5rem;
  cursor: pointer;
  color: #6b7280;
  width: 36px;
  height: 36px;
  border-radius: 6px;
  display: flex;
  align-items: center;
  justify-content: center;
  transition: all 0.2s ease;
}

.close-btn:hover {
  background-color: #f3f4f6;
  color: #1f2937;
}

.close-btn:active {
  background-color: #e5e7eb;
}

/* Modal Body */
.modal-body {
  padding: 24px;
  flex: 1;
  overflow-y: auto;
}

/* Form Rows */
.form-row {
  display: grid;
  grid-template-columns: 1fr;
  gap: 16px;
  margin-bottom: 20px;
}

.form-row:has(.form-group:nth-child(2)) {
  grid-template-columns: 1fr 1fr;
}

/* Form Group */
.form-group {
  display: flex;
  flex-direction: column;
}

.form-group label {
  display: block;
  margin-bottom: 8px;
  font-weight: 500;
  font-size: 0.875rem;
  color: #374151;
  letter-spacing: 0.01em;
}

.form-group label.required::after {
  content: " *";
  color: #ef4444;
}

/* Form Control */
.form-control {
  width: 100%;
  padding: 10px 12px;
  border: 1.5px solid #d1d5db;
  border-radius: 8px;
  font-size: 0.938rem;
  color: #1f2937;
  background-color: white;
  transition: all 0.2s ease;
  box-sizing: border-box;
}

.form-control::placeholder {
  color: #9ca3af;
}

.form-control:hover {
  border-color: #9ca3af;
}

.form-control:focus {
  outline: none;
  border-color: #3b82f6;
  box-shadow: 0 0 0 3px rgba(59, 130, 246, 0.1);
}

.form-control:disabled {
  background-color: #f3f4f6;
  cursor: not-allowed;
  opacity: 0.6;
}

/* Checkbox Group */
.checkbox-group {
  padding-top: 8px;
}

.checkbox-label {
  display: inline-flex;
  align-items: center;
  cursor: pointer;
  user-select: none;
  padding: 8px 12px;
  border-radius: 8px;
  transition: background-color 0.2s ease;
}

.checkbox-label:hover {
  background-color: #f9fafb;
}

.checkbox-input {
  width: 18px;
  height: 18px;
  margin: 0;
  cursor: pointer;
  accent-color: #3b82f6;
}

.checkbox-text {
  margin-left: 10px;
  font-size: 0.938rem;
  color: #374151;
  font-weight: 500;
}

/* Modal Footer */
.modal-footer {
  display: flex;
  justify-content: flex-end;
  gap: 12px;
  padding: 16px 24px 24px;
  border-top: 1px solid #e5e7eb;
  background-color: #f9fafb;
  border-radius: 0 0 12px 12px;
}

/* Responsive */
@media (max-width: 640px) {
  .modal-content {
    width: 100%;
    max-height: 100vh;
    border-radius: 0;
  }

  .modal-header {
    padding: 20px 16px 12px;
  }

  .modal-header h3 {
    font-size: 1.25rem;
  }

  .modal-body {
    padding: 16px;
  }

  .form-row:has(.form-group:nth-child(2)) {
    grid-template-columns: 1fr;
  }

  .modal-footer {
    padding: 12px 16px 16px;
    flex-direction: column-reverse;
  }

  .modal-footer button {
    width: 100%;
  }
}

/* Scrollbar Styling */
.modal-content::-webkit-scrollbar {
  width: 8px;
}

.modal-content::-webkit-scrollbar-track {
  background: #f3f4f6;
}

.modal-content::-webkit-scrollbar-thumb {
  background: #d1d5db;
  border-radius: 4px;
}

.modal-content::-webkit-scrollbar-thumb:hover {
  background: #9ca3af;
}
</style>