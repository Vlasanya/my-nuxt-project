import { faStar } from '@fortawesome/free-solid-svg-icons';
import 'bootstrap/dist/css/bootstrap.css'


<template>
  <div class="container mt-4">
    <!-- Додайте рейтинг іконки зірки відповідно до оцінки, наприклад, 4 бали -->
    <font-awesome-icon icon="fa-solid fa-star" v-for="star in 4" :key="star" />
  </div>
</template>

<script>
import { library } from '@fortawesome/fontawesome-svg-core';
import { faStar } from '@fortawesome/free-solid-svg-icons';
import 'bootstrap/dist/css/bootstrap.css';

library.add(faStar);

export default {};
</script>


