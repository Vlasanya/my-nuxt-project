import 'bootstrap/dist/css/bootstrap.css'

<template>
  <div class="service-form">
    <form @submit.prevent="submitForm">
      <div class="mb-3">
        <label for="service-name" class="form-label">Service Name:</label>
        <input type="text" class="form-control" id="service-name" v-model="formData.serviceName" required />
      </div>

      <div class="mb-3">
        <label for="business-name" class="form-label">Business Name:</label>
        <input type="text" class="form-control" id="business-name" v-model="formData.businessName" required />
      </div>

      <div class="mb-3">
        <label for="service-rating" class="form-label">Service Rating:</label>
        <input type="number" class="form-control" id="service-rating" v-model="formData.serviceRating" min="0" max="5" required />
      </div>

      <!-- Додаємо компонент Rating з власністю rating, яка зв'язана з formData.serviceRating -->
      <Rating :rating="formData.serviceRating" />

      <button type="submit" class="btn btn-primary">Submit Data</button>
    </form>
  </div>
</template>

<script>
import Rating from '@/components/Rating.vue';

export default {
  components: {
    Rating,
  },
  data() {
    return {
      formData: {
        serviceName: "",
        businessName: "",
        serviceRating: null,
      },
    };
  },
  methods: {
    async submitForm() {
      try {
        await this.$store.dispatch("getForms", this.formData);
        // Форма була успішно відправлена
        this.$router.push("/");
      } catch (error) {
        // Обробка помилок
        this.$store.commit("setFormError", error.message); // Встановлюємо повідомлення про помилку
        console.error("Помилка при відправленні форми:", error);
      }
    },
  },
};
</script>

