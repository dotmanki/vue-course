<script setup lang="ts">
import { Cart } from '@models/Cart.model'
interface Props {
  cart: Cart[]
}

const { cart } = defineProps<Props>()
</script>
<template>
  <div id="carrito" class="bg-white p-3">
    <p class="text-center">
      {{ cart.length === 0 && 'El carrito esta vacio' }}
    </p>
    <table class="w-100 table">
      <thead>
        <tr>
          <th>Imagen</th>
          <th>Nombre</th>
          <th>Precio</th>
          <th>Cantidad</th>
          <th></th>
        </tr>
      </thead>
      <tbody>
        <!-- <tr>
                    <td>
                      <img
                        class="img-fluid"
                        src="/img/guitarra_02.jpg"
                        alt="imagen guitarra"
                      />
                    </td>
                    <td>SRV</td>
                    <td class="fw-bold">$299</td>
                    <td class="flex align-items-start gap-4">
                      <button type="button" class="btn btn-dark">-</button>
                      1
                      <button type="button" class="btn btn-dark">+</button>
                    </td>
                    <td>
                      <button class="btn btn-danger" type="button">X</button>
                    </td>
                  </tr> -->
      </tbody>
    </table>

    <p class="text-end">Total pagar: <span class="fw-bold">$899</span></p>
    <button class="btn btn-dark w-100 mt-3 p-2">Vaciar Carrito</button>
  </div>
</template>
