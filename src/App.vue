<template>
  <div>
    <div class="focus">
      <input type="text" ref="inputRef" />
      <div class="button-container">
        <button @click="inputFieldFocus">Focus</button>
        <button @click="toggleModal()">Open Modal</button>
      </div>
      <div class="theme-button-container">
        <button @click="setTheme('sales')">Set Theme</button>
        <button @click="removeTheme()">Remove Theme</button>
      </div>
    </div>

    <ThemeModal :isModalVisible="showModal" :title="modalTitle" :content="modalContent"
      :theme="modalTheme || defaultTheme" @closeModal="toggleModal">
      <h3>Hi! from slot</h3>
      <template v-slot:links>
        <a href="#" class="link-button">Link 1</a>
        <a href="#" class="link-button">Link 2</a>
      </template>
    </ThemeModal>
  </div>
</template>

<script>
import ThemeModal from './components/ThemeModal.vue';

export default {
  name: 'App',
  components: {
    ThemeModal,
  },
  data() {
    return {
      showModal: false,
      modalTitle: 'Sign up for the Giveaway!',
      modalContent: 'Grab your ninja swag for half price!',
      modalTheme: null,
      defaultTheme: 'default',
    };
  },
  methods: {
    inputFieldFocus() {
      this.$refs.inputRef.focus();
    },
    toggleModal() {
      this.showModal = !this.showModal;
    },
    setTheme(theme) {
      this.modalTheme = theme;
      window.alert(`Current modal theme: ${this.modalTheme}`);
    },
    removeTheme() {
      if (this.modalTheme === 'sales') {
        this.modalTheme = this.defaultTheme;
      } else {
        this.modalTheme = 'sales';
      }
      window.alert(`Current modal theme: ${this.modalTheme}`);
    },
  },
};
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

input[type="text"] {
  width: 100%;
  padding: 12px;
  border: 1px solid #ddd;
  border-radius: 8px;
  font-size: 16px;
  outline: none;
  transition: border-color 0.3s ease, box-shadow 0.3s ease;
  margin-bottom: 25px;
}

input[type="text"]:focus {
  border-color: #3498db;
  box-shadow: 0 0 6px rgba(52, 152, 219, 0.3);
}

.button-container {
  display: flex;
  justify-content: center;
  gap: 10px;
  margin-top: 10px;
}

button {
  flex: 1;
  min-width: 130px;
  margin-top: 10px;
  background-color: #3498db;
  color: white;
  padding: 10px 15px;
  border: none;
  border-radius: 5px;
  font-size: 14px;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  margin: 10px 0;
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

.theme-button-container {
  display: flex;
  justify-content: center;
  gap: 10px;
  font-size: 14px;
}

.link-button {
  padding: 10px 20px;
  background-color: #3498db;
  color: white;
  text-decoration: none;
  border-radius: 5px;
  display: inline-block;
  border: none;
  cursor: pointer;
  transition: background-color 0.3s ease, transform 0.2s ease;
  margin: 5px;
}

.link-button:hover {
  background-color: #2980b9;
  transform: scale(1.05);
}

.link-button:active {
  background-color: #2471a3;
  transform: scale(0.98);
}

@media (max-width:575px) {
  button {
    flex: 1;
    min-width: 125px;
    margin-top: 10px;
    background-color: #3498db;
    color: white;
    padding: 10px 10px;
    border: none;
    border-radius: 5px;
    font-size: 14px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin: 10px 0;
    display: inline-block;
    text-align: center;
  }
}

@media (max-width:425px) {
  button {
    flex: 1;
    min-width: 108px;
    margin-top: 10px;
    background-color: #3498db;
    color: white;
    padding: 10px 10px;
    border: none;
    border-radius: 5px;
    font-size: 12px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin: 10px 0;
    display: inline-block;
    text-align: center;
  }

  h3 {
    font-size: 14px;
  }
}

@media (max-width:375px) {
  button {
    flex: 1;
    min-width: 92px;
    margin-top: 10px;
    background-color: #3498db;
    color: white;
    padding: 10px 10px;
    border: none;
    border-radius: 5px;
    font-size: 10px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin: 10px 0;
    display: inline-block;
    text-align: center;
  }

  .link-button {
    font-size: 12px;
  }

  h3 {
    font-size: 12px;
  }
}

@media (min-width:1600px) {
  .focus {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    padding: 80px;
    background-color: #ffffff;
    border-radius: 12px;
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.1);
    max-width: 350px;
    margin: 150px auto;
    border: 1px solid #e0e0e0;
    transition: transform 0.3s ease, box-shadow 0.3s ease;
    max-width: 600px;
  }

  input[type="text"] {
    width: 100%;
    padding: 12px;
    border: 1px solid #ddd;
    border-radius: 8px;
    font-size: 40px;
    outline: none;
    transition: border-color 0.3s ease, box-shadow 0.3s ease;
    margin-bottom: 40px;
  }

  input[type="text"]:focus {
    border-color: #3498db;
    box-shadow: 0 0 6px rgba(52, 152, 219, 0.3);
  }

  .button-container {
    display: flex;
    justify-content: center;
    gap: 10px;
    margin-top: 10px;
  }

  button {
    flex: 1;
    min-width: 220px;
    margin-top: 10px;
    background-color: #3498db;
    color: white;
    padding: 15px 20px;
    border: none;
    border-radius: 5px;
    font-size: 25px;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin: 10px 0;
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

  .link-button {
    padding: 10px 20px;
    font-size: 40px;
    background-color: #3498db;
    color: white;
    text-decoration: none;
    border-radius: 5px;
    display: inline-block;
    border: none;
    cursor: pointer;
    transition: background-color 0.3s ease, transform 0.2s ease;
    margin: 5px;
  }

  .link-button:hover {
    background-color: #2980b9;
    transform: scale(1.05);
  }

  .link-button:active {
    background-color: #2471a3;
    transform: scale(0.98);
  }

}
</style>
