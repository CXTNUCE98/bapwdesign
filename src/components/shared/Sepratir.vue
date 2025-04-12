<script setup lang="ts">
const { img, text } = defineProps<{
    img: any
    text: string
}>()

</script>

<template>
    <div class="relative">
        <img :src="img" alt="img-sepratir" class="block h-399px object-cover">
        <div class="text-overlay font-['Volkhov']">
            {{ text }}
        </div>
    </div>
</template>
<style scoped>
.text-overlay {
    position: absolute;
    top: 50%;
    left: 30%;
    width: 560px;
    transform: translate(-50%, -50%);
    color: white;
    font-size: 50px;
    font-weight: bold;
}
</style>