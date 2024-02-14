<template>
  <MainLayout>
    <div id="IndexPage" class="mx-auto mt-4 max-w-[1200px] px-2" />
    <div
      v-if="products"
      class="grid xl:grid-cols-6 lg:grid-cols-5 md:grid-cols-4 sm:grid-cols-3 grid-cols-2 gap-4"
    >
      <div v-for="product in products" :key="product">
        <ProductComponent :product="product" />
      </div>
    </div>
  </MainLayout>
</template>

<script setup>
import MainLayout from '~/layouts/MainLayout.vue'
import ProductComponent from '~/components/BaseProductComponent.vue'

const products = [
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/70/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/71/800/800',
    price: 9699
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/72/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/73/800/800',
    price: 29999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/74/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/75/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/76/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/77/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/78/800/800',
    price: 9999
  },
  {
    id: 1,
    title: 'Title 1',
    description: 'This is a description',
    url: 'https://picsum.photos/id/79/800/800',
    price: 6999
  }
]
</script>
