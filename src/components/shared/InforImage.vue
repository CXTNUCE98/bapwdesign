<script setup lang="ts">
const { note, title, des, redirect, isCenter, isShowButton } = defineProps<{
    note: string
    title: string
    des: string
    redirect?: string
    isCenter?: boolean
    isShowButton?: boolean
}>()
</script>

<template>
    <div class="text-red-400 text-lg font-bold uppercase tracking-widest">{{ note }}</div>
    <div :class="{ 'text-center': isCenter }"
        class="w-[583px] h-[142px] text-indigo-950 text-[50px] font-bold font-['Volkhov'] leading-[71.04px] mb-6">
        {{ title }}</div>
    <p v-if="des" class="w-[583px] h-[103px] text-black text-base font-normal font-['Poppins'] leading-relaxed">Et
        {{ des }}</p>
    <el-button v-if="isShowButton" size="large" color="#DF6951">
        <span class="text-white">
            View Packages
        </span>
    </el-button>
    <slot name="custom" />
</template>