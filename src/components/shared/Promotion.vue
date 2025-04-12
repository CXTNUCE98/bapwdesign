<script setup lang="ts">

const { image, note, title, redirect } = definePropsRefs<{
    image: any
    note: string
    title: string
    redirect?: string
}>()

const router = useRouter()
function goToPackages() {
    console.log('running');
    
    router.push(redirect)
}
</script>

<template>
    <div class="relative">
        <img :src="image" alt="img" class="block w-full h-auto bg-stone-900/opacity-40">
        <div class="absolute inset-0 bg-stone-900 opacity-40"></div>
        <div class="absolute inset-0 flex flex-col items-center justify-center text-center space-y-4">
            <div class="text-rose-50 text-lg font-bold uppercase tracking-widest">
                {{ note }}
            </div>
            <div class="text-white text-[50px] font-bold leading-[71.04px]">
                {{ title }}
            </div>
            <el-button size="large" color="#DF6951" @click="goToPackages">
                <span class="text-white">
                    View Packages
                </span>
            </el-button>
        </div>
    </div>
</template>
<style scoped>
</style>