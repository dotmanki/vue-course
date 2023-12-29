<script setup lang="ts">
import { onMounted, reactive } from 'vue'
import type { Guitar } from './models/Guitar.model'
import type { Cart } from './models/Cart.model'
import { data } from './data/guitars.json'
import Card from './components/Card.vue'
import Header from './components/Header.vue'
import Footer from './components/Footer.vue'

interface Props {
  guitars: Guitar[]
  cart: Cart[]
}

const state = reactive<Props>({
  guitars: [],
  cart: [],
})

onMounted(() => {
  state.guitars = data
})

const addToCart = (id: number) => {
  const guitar = state.guitars.find((guitar) => guitar.id === id)
  if (guitar) {
    const cartGuitar = state.cart.find(
      (cartGuitar) => cartGuitar.productId === guitar.id
    )
    if (cartGuitar) {
      cartGuitar.quantity++
      return
    }
    state.cart.push({ productId: guitar.id, quantity: 1 })
  }
}
</script>

<template>
  <Header :cart="state.cart" />

  <main class="container-xl mt-5">
    <h2 class="text-center">Nuestra Colección</h2>

    <div class="row mt-5">
      <div
        v-for="guitar in state.guitars"
        :key="guitar.id"
        class="col-md-6 col-lg-4 my-4 row align-items-center"
      >
        <Card
          :id="guitar.id"
          :image="guitar.image"
          :name="guitar.name"
          :description="guitar.description"
          :price="guitar.price"
          @addToCart="addToCart"
        />
      </div>
    </div>
  </main>
  <Footer />
</template>

<style scoped></style>
