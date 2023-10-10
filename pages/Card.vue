import 'bootstrap/dist/css/bootstrap.css'

<template>
  <div class="container mt-4">
    <h1>Here can be your card</h1>
    <ServiceCard
      v-for="form in formData"
      :key="form.id"
      :serviceName="form.serviceName"
      :businessName="form.businessName"
      :serviceRating="form.serviceRating"
    />
    <ul>
      <li v-for="form in formData" :key="form.id">
        <p>Service Name: {{ form.serviceName }}</p>
        <p>Business Name: {{ form.businessName }}</p>
        <p>Service Rating: {{ form.serviceRating }}</p>
      </li>
    </ul>
    <div v-if="formSubmitted">Форма відправлена успішно!</div>
    <div v-if="formError">{{ formError }}</div>

    <!-- Додамо форму для додавання нової картки -->
    <div class="mt-4">
      <h2>Add a New Card</h2>
      <form @submit.prevent="addNewCard" class="mb-3">
        <div class="mb-3">
          <label for="new-service-name" class="form-label">Service Name:</label>
          <input type="text" class="form-control" id="new-service-name" v-model="newCard.serviceName" required />
        </div>
        <div class="mb-3">
          <label for="new-business-name" class="form-label">Business Name:</label>
          <input type="text" class="form-control" id="new-business-name" v-model="newCard.businessName" required />
        </div>
        <div class="mb-3">
          <label for="new-service-rating" class="form-label">Service Rating:</label>
          <input type="number" class="form-control" id="new-service-rating" v-model="newCard.serviceRating" min="0" max="5" required />
        </div>
        <button type="submit" class="btn btn-primary">Add Card</button>
      </form>
    </div>
  </div>
</template>

<script>
import { mapState, mapActions } from "vuex";

export default {
  computed: {
    ...mapState(["formData", "formSubmitted", "formError"]),
  },
  data() {
    return {
      newCard: {
        serviceName: "",
        businessName: "",
        serviceRating: null,
      },
    };
  },
  methods: {
    async asyncData({ store }) {
      await store.dispatch("getForms");
    },
    addNewCard() {
      // Додавання нової картки до formData
      this.$store.commit("addForm", this.newCard);
      // Очистити дані для нової картки після додавання
      this.newCard = {
        serviceName: "",
        businessName: "",
        serviceRating: null,
      };
    },
  },
};
</script>
