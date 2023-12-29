<script setup lang="ts">
import { Guitar } from '../models/Guitar.model';



  const props = defineProps<Guitar>()
  defineEmits(['addToCart'])
</script>

<template>
  <div class="col-md-6 col-lg-4 my-4 row align-items-center">
          <div class="col-4">
              <img class="img-fluid" :src="'/img/' + props.image+ '.jpg'" :alt="props.name">
          </div>
          <div class="col-8">
              <h3 class="text-black fs-4 fw-bold text-uppercase">{{ props.name }}</h3>
              <p>{{ props.description }}</p>
              <p class="fw-black text-primary fs-3">${{ props.price }}</p>
              <button
                type="button"
                class="btn btn-dark w-100 "
                @click="$emit('addToCart', props.id)"
              >agregar al Carrito</button>
          </div>
        </div>  
</template>