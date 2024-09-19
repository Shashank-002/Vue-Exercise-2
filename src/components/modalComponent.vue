<template>
  <div class="modal-overlay" v-if="isVisible" @click.self="closeModal">
    <div :class="['modal-content', themeClass]">
      <h2 :class="['modal-title', themeClass]">{{ title }}</h2>
      <p :class="['modal-body', themeClass]">{{ content }}</p>
      <slot></slot> 
    </div>
  </div>
</template>

<script>
export default {
  name: 'ModalComponent',
  props: {
    isVisible: {
      type: Boolean,
      required: true,
    },
    title: {
      type: String,
      default: 'Modal Title',
    },
    content: {
      type: String,
      default: 'modal Content',
    },
    theme: {
      type: String,
      default: null,
    },
  },
  computed: {
    themeClass() {
      return this.theme === 'sales' ? 'sales-theme' : '';
    },
  },
  methods: {
    closeModal() {
      this.$emit('closeModal');
    },
  },
};
</script>

<style scoped>
.modal-overlay {
  position: fixed;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  background-color: rgba(0, 0, 0, 0.5);
  display: flex;
  justify-content: center;
  align-items: center;
}

.modal-content {
  background-color: #fff;
  padding: 30px;
  margin-top: -280px;
  border-radius: 12px;
  max-width: 500px;
  width: 100%;
  text-align: center;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
}

.modal-title {
  font-size: 2em;
  font-weight: bold;
  color: #1abc9c;
  margin-bottom: 15px;
}

.modal-body {
  font-size: 1.2em;
  color: #666;
  margin-bottom: 20px;
}

.sales-theme.modal-content {
  background-color: red;
}

.sales-theme.modal-title {
  color: white;
}

.sales-theme.modal-body {
  color: white;
}

button {
  margin-top: 20px;
  padding: 10px 20px;
  background-color: #3498db;
  color: #fff;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background-color 0.3s ease;
}

button:hover {
  background-color: #2980b9;
}
</style>
