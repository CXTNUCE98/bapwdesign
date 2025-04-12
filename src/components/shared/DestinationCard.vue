<script lang="ts" setup>
const { product } = defineProps<{
    product: {
        id: string
        name: string
        img: string
        router: {
            mainPath: string
            micro: string
            query: string
        }
        price: number
    }
}>()

const emit = defineEmits(['openDetail'])

function openTourDetail() {
    emit('openDetail')    
}
</script>

<template>
    <div class="card border-border rounded-2xl leading-normal! hover:shadow-lg hover:-translate-y-3 cursor-pointer">
        <img :src="product?.img" @click="openTourDetail" class="block object-cover h-full rounded-12px w-full">
        <div class="text-overlay w-[83px] h-[35px] bg-gradient-to-r from-red-400 to-orange-700 rounded-[46px]">
            <span class="text-white text-base font-light">${{ product?.price }}</span>
        </div>
    </div>
</template>

<style scoped>
.card {
    height: 237px;
    min-width: 232px;
    border: 1px solid var(--el-border-color);
    box-sizing: border-box;
    text-align: center;
    position: relative;
    transition: all .3s ease-in-out;
    bottom: 0;
    margin: auto;
}

.text-overlay {
    position: absolute;
    top: 30px;
    right: -30px;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 16px;
    font-weight: bold;
    display: flex;
    align-items: center;
    justify-content: center;
}
</style>
