<script setup lang="ts">
const { note, title } = defineProps<{
    note: string
    title: string
}>()

</script>
<template>
    <div class="text-18px text-#DF6951 font-semibold">
        {{ note }}
    </div>
    <div class="text-#181E4B text-50px font-bold">
        {{ title }}
    </div>
    <slot name="content"></slot>
</template>



<style scoped></style>