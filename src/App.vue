<template>
  <div>
    <div class="focus">
      <input type="text" ref="inputRef">
      <br><br>
      <button @click="inputFieldFocus">Focus</button>
      <button @click="showModal = true">Open Modal</button>
    </div>
    <Modal :isVisible="showModal" @close="showModal = false" />
  </div>

</template>

<script>
import Modal from './components/modalComponent.vue';
export default {
  name: 'App',
  components: {
    Modal
  },
  methods: {
    inputFieldFocus() {
      this.$refs.inputRef.focus();
    }
  },
  data() {
    return {
      showModal: false,
    };
  },
}
</script>

<style scoped>
.focus {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  padding: 40px;
  background-color: #ffffff;
  border-radius: 12px;
  box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
  max-width: 350px;
  margin: 50px auto;
  border: 1px solid #e0e0e0;
  transition: transform 0.3s ease, box-shadow 0.3s ease;
}

.focus:hover {
  transform: translateY(-10px);
  box-shadow: 0 12px 24px rgba(0, 0, 0, 0.2);
}

input[type="text"] {
  width: 100%;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
}

input[type="text"]:focus {
  border-color: #3498db;
  box-shadow: 0 0 6px rgba(52, 152, 219, 0.3);
}

button {
  background-color: #3498db;
  color: white;
  padding: 10px 20px;
  border: none;
  border-radius: 5px;
  font-size: 16px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  margin: 10px 0px;
  display: inline-block;
  text-align: center;
}

button:hover {
  background-color: #2980b9;
  transform: scale(1.05);
}

button:active {
  background-color: #2471a3;
  transform: scale(0.98);
}
</style>
