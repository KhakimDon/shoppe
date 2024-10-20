<script setup>
import { useProductsStore } from '@/stores/products';
import { ref } from 'vue';

const productStore = useProductsStore()

</script>

<template>
    <main class="catalog w-[100%]">
        <div class="catalog__wrapper h-[100%] w-[1248px] mt-[96px] m-auto flex relative">
            <!-- left filter -->
            <div class="catalog__wrapper__left h-[500px] flex flex-col w-[262px] sticky top-0">
                <h3 class="text-[33px] font-[500]">Shop The Latest</h3>
                <!-- input -->
                <div class="w-[261px] h-[35px] mt-[20px] flex items-center justify-between relative">
                    <input placeholder="Search..." type="text"
                        class="outline-none w-[261px] h-[35px] py-[11px] text-[14px] border-b-[1px] border-solid border-[#D8D8D8] bg-[transparent]"
                        name="" id="">
                    <button class="absolute right-[0]">
                        <svg fill="none" height="19px" width="19px" viewBox="0 0 24 24" stroke-width="1.5"
                            stroke="black" class="size-6">
                            <path stroke-linecap="round" stroke-linejoin="round"
                                d="m21 21-5.197-5.197m0 0A7.5 7.5 0 1 0 5.196 5.196a7.5 7.5 0 0 0 10.607 10.607Z" />
                        </svg>

                    </button>
                </div>
                <!-- filter, sale, options -->
                <div class="mt-[39px]">
                    <select
                        class="h-[53px] w-[261px] px-[12px] py-[15px] text-[14px] outline-none cursor-pointer rounded-[4px] border-[1px] border-solid border-[#D8D8D8]"
                        name="" id="">
                        <option disabled selected class="" value="">Shop By</option>
                        <option class="opt bg-blue" value="">Shop By</option>
                    </select>
                    <select
                        class="h-[53px] mt-[16px] w-[261px] pl-[12px] py-[15px] text-[14px] outline-none cursor-pointer rounded-[4px] border-[1px] border-solid border-[#D8D8D8]"
                        name="" id="">
                        <option disabled selected class="" value="">Sort By</option>
                        <option class="opt bg-blue" value="">Sort By</option>
                    </select>
                    <div class="flex flex-col mt-[39px]">
                        <div class="w-[262px] reltive flex items-center ">

                            <div class="line h-[10px] w-[1px] bg-[#D8D8D8]"></div>
                            <input @input="change()" type="range" min="40" max="180" step="1" class="rangeInput">
                            <div class="line h-[11px] w-[1px] bg-[#D8D8D8]"></div>

                        </div>
                        <div class="mt-[8px] flex justify-between">
                            <span class="text-[#707070] text-[14px]">Price: $40 - $180</span>
                            <button class="text-[#A18A68] text-[14px]">Filter</button>
                        </div>

                    </div>
                    <div class="mt-[39px] flex w-[100%] items-center justify-between">
                        <span>On sale</span>
                        <button class="h-[20px] w-[33px] bg-[#707070] rounded-[16px]">
                            <div class="rounded-[50%] h-[14px] w-[14px] m-[3px] bg-[#fff]">
                            </div>
                        </button>
                    </div>
                    <div class="mt-[30px] flex w-[100%] items-center justify-between">
                        <span>In stock</span>
                        <button class="h-[20px] w-[33px] bg-[#707070] rounded-[16px]">
                            <div class="rounded-[50%] h-[14px] w-[14px] m-[3px] bg-[#fff]">
                            </div>
                        </button>
                    </div>
                </div>

            </div>
            <!-- right goods -->

            <div class="catalog__wrapper__right h-[100%] ml-[35px] flex flex-wrap gap-[24px] pt-[70px]">
                <!-- block -->
                <div v-for="item of productStore.products" :key="item.id"
                    class="h-[392px] cursor-pointer border-b-[1px] border-solid border-[#707070] w-[300px] flex flex-col items-start relative">
                    <img class="rounded-[8px] h-[300px] w-[100%] bg-[red]" :src="item.img[0]" :alt="item.title">
                    <!-- discount -->
                    <div v-show="item.discount > 1" class="absolute mt-[16px] text-center ml-[12px] h-[24px] w-[46px] bg-[#A18A68] rounded-[4px] py-[3px] text-[12px] text-[#fff]">-{{ item.discount }}%</div>
                    <!-- sold out - quantity -->
                    <div v-show="item.quantity < 1" class="absolute mt-[16px] text-center ml-[12px] h-[24px] w-[64px] bg-[#A18A68] rounded-[4px] py-[3px] text-[12px] text-[#fff]">Sold out</div>

                    <h3 class="mt-[12px] text-[20px]">{{ item.title }}</h3>
                    <p class="mt-[7px] text-[20px] text-[#A18A68]">$ {{ item.price }}</p>
                </div>
            </div>

        </div>
    </main>
</template>

<style scoped>
.rangeInput {
    -webkit-appearance: none;
    width: 100%;
    height: 1px;
    border-radius: 0px;
    background: #D8D8D8;
    outline: none;
    opacity: 0.7;
    -webkit-transition: .2s;
    transition: opacity .2s;
}

.rangeInput:hover {
    opacity: 1;
}

.rangeInput::-webkit-slider-thumb {
    -webkit-appearance: none;
    appearance: none;
    width: 14px;
    height: 14px;
    border-radius: 50%;
    background: #000;
    cursor: pointer;
}

.rangeInput::-moz-range-thumb {
    width: 14px;
    height: 14px;
    border-radius: 50%;
    background: #000;
    cursor: pointer;
}
</style>
