<template>
  <div class="modal-overlay" v-if="isModalVisible" @click.self="closeModal">
    <div :class="['modal-content', themeClass]">
      <h2 :class="['modal-title', themeClass]">{{ title }}</h2>
      <p :class="['modal-body', themeClass]">{{ content }}</p>
      <h3 :class="h3ThemeClass">
        <slot />
      </h3>
      <slot name="links"></slot>
    </div>
  </div>
</template>

<script>
export default {
  name: 'ThemeModal',
  props: {
    isModalVisible: {
      type: Boolean,
      required: true,
    },
    title: {
      type: String,
      default: 'Modal Title',
    },
    content: {
      type: String,
      default: 'Modal Content',
    },
    theme: {
      type: String,
      default: null,
    },
  },
  computed: {
    themeClass() {
      if (this.theme === 'sales') return 'sales-theme';
      if (this.theme === 'default') return 'default-theme';
      return '';
    },
    h3ThemeClass() {
      return this.theme === 'sales' ? 'sales-color' : 'default-color';
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
  margin-top: -330px;
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
  font-size: 36px;
}

.sales-theme.modal-body {
  color: white;
}

.sales-color {
  color: white;
}

.default-color {
  color: gray;
}

@media (max-width: 1024px) and (min-width: 900px) {
  .modal-content {
    margin-top: -250px;
    height: 220px;
  }
}

@media (max-width:768px) {
  .modal-content {
    margin-top: -250px;
    height: 220px;
  }
}

@media (max-width:575px) {

  .modal-content {
    margin-top: -250px;
    height: 200px;
    max-width: 340px;
  }

  .modal-title {
    font-size: 28px;
    font-weight: bold;
    color: #1abc9c;
    margin-bottom: 15px;
  }

  .modal-body {
    font-size: 18px;
    color: #666;
    margin-bottom: 20px;
  }

  .sales-theme.modal-content {
    background-color: red;
    max-width: 340px;
    height: 200px;
  }

  .sales-theme.modal-title {
    color: white;
    font-size: 28px;
  }

  .sales-theme.modal-body {
    color: white;
    font-size: 18px;
  }
}

@media (max-width:425px) {
  .modal-content {
    margin-top: -250px;
    height: 180px;
    max-width: 280px;
  }

  .modal-title {
    font-weight: bold;
    color: #1abc9c;
    font-size: 24px;
  }

  .modal-body {
    font-size: 16px;
    color: #666;
    margin-bottom: 16px;
  }

  .sales-theme.modal-content {
    background-color: red;
    max-width: 280px;
  }

  .sales-theme.modal-title {
    color: white;
    font-size: 24px;
  }

  .sales-theme.modal-body {
    color: white;
    font-size: 16px;
  }
}

@media (max-width:375px) {
  .modal-content {
    margin-top: -250px;
    height: 150px;
    max-width: 240px;
  }

  .modal-title {
    font-weight: bold;
    color: #1abc9c;
    font-size: 20px;
  }

  .modal-body {
    font-size: 12px;
    color: #666;
    margin-bottom: 12px;
  }

  .sales-theme.modal-content {
    background-color: red;
    max-width: 240px;
    height: 150px;
  }

  .sales-theme.modal-title {
    color: white;
    font-size: 20px;
  }

  .sales-theme.modal-body {
    color: white;
    font-size: 12px;
  }
}

@media (min-width:1600px) {
  .modal-content {
    background-color: #fff;
    padding: 30px;
    margin-top: -700px;
    border-radius: 12px;
    max-width: 850px;
    height: 360px;
    text-align: center;
    box-shadow: 0 6px 12px rgba(0, 0, 0, 0.2);
  }

  .modal-title {
    font-size: 65px;
    font-weight: bold;
    color: #1abc9c;
    margin-bottom: 15px;
  }

  .modal-body {
    font-size: 35px;
    color: #666;
    margin-bottom: 20px;
  }

  .sales-theme.modal-content {
    background-color: red;
  }

  .sales-theme.modal-title {
    color: white;
    font-size: 65px;
  }

  .sales-theme.modal-body {
    color: white;
    font-size: 35px;
  }
}
</style>
