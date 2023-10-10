import 'bootstrap/dist/css/bootstrap.css'


<template>
  <div class="service-card">
    <h2>{{ serviceName }}</h2>
    <p>Business Name: {{ businessName }}</p>
    <p>Service Rating: {{ serviceRating }} </p>
    <font-awesome-icon :icon="['far', 'star']" class="star" />
  </div>
</template>

<script>
export default {
  props: {
    serviceName: String,
    businessName: String,
    serviceRating: Number
  }
};
</script>

<style scoped>
.service-card {
  border: 1px solid #ddd;
  padding: 15px;
  margin-bottom: 20px;
  box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
}

.star {
  display: inline-block;
  width: 42px;
  height: 42px;
  color: black;
  margin-left: 10px;
}
</style>
