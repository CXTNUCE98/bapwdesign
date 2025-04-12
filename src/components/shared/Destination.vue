<script setup lang="ts">
import emblaCarouselVue from 'embla-carousel-vue'
import Autoplay from 'embla-carousel-autoplay'

const [emblaRef] = emblaCarouselVue({ loop: true, align: 'start' }, [Autoplay()])

import Watch from "@/public/watch-london.png"
import Italia from "@/public/italia.png"
import Colosseum from "@/public/colosseum.png"
import Berlin from "@/public/berlin.png"


const destinations = [
    {
        img: Watch,
        name: 'London Watch',
        price: 700,
    },
    {
        img: Italia,
        name: 'The Ijssel River',
        price: 800,
    },
    {
        img: Colosseum,
        name: 'The Colosseum',
        price: 500,
    },
    {
        img: Berlin,
        name: 'Berlin Cathedral',
        price: 400,
    },
    {
        img: 'https://i.pinimg.com/564x/10/65/ea/1065ea567e8cc827cae58745544cedb8.jpg',
        name: 'Statue of Liberty',
        price: 500,
    },
    {
        img: 'https://i.pinimg.com/564x/be/6c/ac/be6cace4c7bef47dcf08f3a9682ae09b.jpg',
        name: 'The Dead Sea',
        price: 400,
    },
    {
        img: 'https://i.pinimg.com/564x/6d/e1/b0/6de1b02945d6477a175e8a3599f21f14.jpg',
        name: "Saint Basil's Cathedral",
        price: 500,
    },
    {
        img: 'https://i.pinimg.com/564x/ae/a9/f7/aea9f71a19c31d183d8fb322c779d1a2.jpg',
        name: 'Machu Picchu',
        price: 400,
    },
    {
        img: 'https://vietsensetravel.com/view/at_kham-pha-tuong-dai-bang-lon-nhat-the-gioi-tai-an-do_523f2979c2c8ddb49bd93794a65db09b.jpg',
        name: 'Giant Jatayu Eagle Statue',
        price: 400,
    },
    {
        img: 'https://i.pinimg.com/564x/ec/ad/b2/ecadb2cc4a5bc891f8486a5b4e848334.jpg',
        name: 'Pisa tower',
        price: 400,
    },
]

const isShowTourDetail = ref(false)
const detail = ref()

function openDetail(info: any) {    
    detail.value = info
    console.log('detail: ', detail);
    isShowTourDetail.value = true
    
}
</script>

<template>
    <div class="carousel-container" >
        <div class="relative embla" ref="emblaRef" >
            <div class="embla__container">
                <div v-for="(item, index) in destinations" :key="index" class="basis-1/1 px-2 py-4 2xl:basis-1/5 lg:basis-1/3 md:basis-1/2 xl:basis-1/4">
                    <SharedDestinationCard :product="item" @openDetail="openDetail(item)"/>
                </div>
            </div>
        </div>
    </div>

    <TourDetailDialog :visible="isShowTourDetail" :info="detail" @close="isShowTourDetail = false"/>
</template>

<style scoped>
.carousel-container {
    width: 1000px;
    overflow: hidden;
    position: absolute;
    margin: 0 auto;
}

.embla {
    overflow: hidden;
}

.embla__container {
    display: flex;
}

.embla__slide {
    flex: 0 0 auto;
    width: 100%;
    min-width: 0;
}
</style>