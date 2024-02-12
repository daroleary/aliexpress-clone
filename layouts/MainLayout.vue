<template>
  <div id="MainLayout" class="fixed z-50 w-full">
    <div id="TopMenu" class="w-full border-b bg-[#FAFAFA] md:block hidden">
      <ul
        class="flex h-10 max-w-[1200px] items-center justify-end bg-[#FAFAFA] px-2 text-xs font-light text-[#333333]"
      >
        <li class="cursor-pointer border-r border-r-gray-400 px-3 hover:text-[#FF4636]">
          Sell on AliExpress
        </li>
        <li class="cursor-pointer border-r border-r-gray-400 px-3 hover:text-[#FF4636]">
          Cookie Preferences
        </li>
        <li class="cursor-pointer border-r border-r-gray-400 px-3 hover:text-[#FF4636]">Help</li>
        <li class="cursor-pointer border-r border-r-gray-400 px-3 hover:text-[#FF4636]">
          Buyer Protection
        </li>
        <li class="px-3 hover:text-[#FF4646] cursor-pointer">
          <Icon name="ic:sharp-install-mobile" size="17" />
          App
        </li>
        <li
          class="relative flex items-center px-2.5 hover:text-[#FF4646] h-full cursor-pointer"
          :class="
            isAccountMenu
              ? 'bg-white border z-40 shadow-[0_15px_100px_40px_rgba(0,0,0,0.3)]'
              : 'border border-[#FAFAFA]'
          "
          @mouseenter="isAccountMenu = true"
          @mouseleave="isAccountMenu = false"
        >
          <Icon name="ph:user-thin" size="17" />
          Account
          <Icon name="mdi:chevron-down" size="15" class="ml-5" />
          <div
            v-if="isAccountMenu"
            id="AccountMenu"
            class="absolute bg-white w-[220px] text-[#333333] z-40 top-[38px] -left-[100px] border-x border-b"
          >
            <div v-if="true">
              <div class="text-semibold text-[15px] my-4 px-3">Welcome to AliExpress!</div>
              <div class="flex items-center gap-1 px-3 mb-3">
                <NuxtLink
                  to="/auth"
                  class="bg-[#FF4646] text-center w-full text-[16px] rounded-sm text-white font-semibold"
                >
                  Login / Register
                </NuxtLink>
              </div>
            </div>
            <div class="border-b" />
            <ul class="bg-white">
              <li
                class="text-[13px]py-2 px-4 w-full hover:bg-gray-200"
                @click="navigateTo('/orders')"
              >
                My Orders
              </li>
              <li v-if="true" class="text-[13px] py-2 px-4 w-full hover:bg-gray-200">Sign Out</li>
            </ul>
          </div>
        </li>
      </ul>
    </div>
    <div id="MainHeader" class="flex items-center w-full bg-white">
      <div
        class="flex lg:justify-start justify-between gap-10 max-w-[1150px] w-full px-3 py-5 mx-auto"
      >
        <NuxtLink to="/" class="flex items-center">
          <img src="/AliExpress-logo.png" alt="AliExpress" width="170" />
        </NuxtLink>

        <div class="max-w-[700px] w-full md:block hidden">
          <div class="relative">
            <div class="flex items-center border-2 border-[#FF4646] rounded-md w-full">
              <input
                v-model="searchItem"
                class="w-full placeholder-gray-400 text-sm pl-3 focus:outline-none"
                type="text"
                placeholder="kitchen accessories"
              />
              <Icon v-if="isSearching" name="eos-icons:loading" size="25" class="mr-2" />
              <button class="flex items-center h-[100%] p-1.5 px-2 bg-[#FF4646]">
                <Icon name="ph:magnifying-glass" size="20" color="#ffffff" />
              </button>
            </div>
            <div
              class="absolute bg-white max-w-[700px] h-auto w-full cursor-pointer hover:bg-gray-100"
            >
              <div v-if="false" class="p-1">
                <NuxtLink
                  to="`/item/1`"
                  class="flex items-center justify-between w-full cursor-pointer hover:bg-gray-100"
                >
                  <div class="flex items-center">
                    <img class="rounded-md" width="40" src="https://picsum.photos/id/82/300/300" />
                    <div class="truncate ml-2">TESTING</div>
                  </div>
                  <div class="truncate">$ 98.99</div>
                </NuxtLink>
              </div>
            </div>
          </div>
        </div>
        <NuxtLink to="/shoppingcart" class="flex items-center">
          <button
            class="relative md:block hidden"
            @mouseenter="isCartHover = true"
            @mouseleave="isCartHover = false"
          >
            <span
              class="absolute flex items-center justify-center -right-[3px] top-0 bg-[#FF4646] h-[17px] min-w-[17px] text-xs text-white px-0.5 rounded-full"
            >
              0
            </span>
            <div class="min-w-[40px]">
              <Icon
                name="ph:shopping-cart-simple-light"
                size="33"
                :color="isCartHover ? '#FF4646' : ''"
              />
            </div>
          </button>
        </NuxtLink>
        <button
          class="md:hidden block rounded-full p-1.5 -mt-[4px] hover:bg-gray-200"
          @click="userStore.isMenuOverlay = true"
        >
          <Icon name="radix-icons:hamburger-menu" size="33" />
        </button>
      </div>
    </div>

    <Loading v-if="userStore.isLoading" />

    <div class="lg:pt-[150px] md:pt-[130px] pt-[80px]" />
    <slot />

    <Footer v-if="!userStore.isLoading" />
  </div>
</template>

<script setup>
import { useUserStore } from '~/stores/user'
const userStore = useUserStore()

const isAccountMenu = ref(false)
const isCartHover = ref(false)
const isSearching = ref(true)
const searchItem = ref('')

import Loading from '~/components/BaseLoading.vue'
import Footer from '~/components/BaseFooter.vue'
</script>
