<template>
  <div class="modal-overlay" v-if="isVisible" @click.self="closeModal">
    <div :class="['modal-content', themeClass]">
      <h2 :class="['modal-title', themeClass]">{{ title }}</h2>
      <p :class="['modal-body', themeClass]">{{ content }}</p>
      <slot></slot>
      <slot name="links"></slot>
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
  margin-top: -350px;
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

@media (max-width: 1024px) and (min-width: 900px)
{
  .modal-content {
  margin-top: -300px;
  height: 170px;
}
}

@media (max-width:575px) {
  .sales-theme.modal-content {
    background-color: red;
    max-width: 340px;
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
  .sales-theme.modal-content {
    background-color: red;
    max-width: 240px;
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

@media (min-width:1600px)
{
  .modal-content {
  background-color: #fff;
  padding: 30px;
  margin-top: -800px;
  border-radius: 12px;
  max-width: 850px;
  height: 330px;
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
