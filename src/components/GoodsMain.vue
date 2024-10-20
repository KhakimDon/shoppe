<script setup>
import { useProductsStore } from '@/stores/products';
import { ref } from 'vue';

const productStore = useProductsStore()



</script>

<template>
    <div class="h-[1170px] w-[100%] pt-[64px]">
        <div class="h-[100%] w-[1248px] m-auto flex flex-col">

            <div class="texts w-[100%] flex justify-between items-center">
                <h2 class="text-[33px] font-[550]">Shop The Latest</h2>
                <button class="text-[#A18A68] text-[20px] font-[500]">View All</button>
            </div>

            <!-- blocks -->

            <div  class="block cursor-pointer h-[100%] w-[100%] mt-[40px] flex flex-wrap gap-[57px]">
                <!-- block -->
                <div v-for="item of productStore.products" :key="item.id" class="h-[472px] border-b-[1px] border-solid border-[#707070] w-[377px] flex flex-col items-start">
                    <img class="rounded-[8px] h-[380px] w-[100%] bg-[gray]" :src="item.img[0]" :alt="item.title">
                    <h3 class="mt-[12px] text-[20px]">{{ item.title }}</h3>
                    <p class="mt-[7px] text-[20px] text-[#A18A68]">$ {{ item.price }}</p>
                </div>
            </div>

        </div>
    </div>
</template>


<style scoped></style>