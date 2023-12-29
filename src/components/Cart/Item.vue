<script setup lang="ts">
import { defineProps } from 'vue'
import type { Guitar } from '../../models/Guitar.model'
interface Props {
  product: Guitar
  quantity: number
}
const { product, quantity } = defineProps<Props>()
</script>
<template lang="">
  <tr>
    <td>
      <img
        class="img-fluid"
        :src="'/img/' + product.image + '.jpg'"
        :alt="product.name"
      />
    </td>
    <td>{{ product.name }}</td>
    <td class="fw-bold">{{ product.price }}</td>
    <td class="flex align-items-start gap-4">
      <button type="button" class="btn btn-dark">-</button>
      {{ quantity }}
      <button type="button" class="btn btn-dark">+</button>
    </td>
    <td>
      <button class="btn btn-danger" type="button">X</button>
    </td>
  </tr>
</template>
