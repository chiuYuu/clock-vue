<script>
import Clock from '@/components/Clock.vue';

export default {
    components: {
        Clock,
    },

    data() {
        return {
            regions: [
                { name: '泰國', timeZone: 'Asia/Bangkok' },
                { name: '台灣', timeZone: 'Asia/Taipei' },
                { name: '新加坡', timeZone: 'Asia/Singapore' },
                { name: '日本', timeZone: 'Asia/Tokyo' },
            ],
        };
    },

}
</script>

<template>
    <section class="container">
        <Clock v-for="(country, index) in regions" :key="index" :region="country.name" :timeZone="country.timeZone" />
    </section>
</template>

<style scoped>
.container {
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    height: 100vh;
    font-family: 'clockicons';
    background-color: #000;
    color: #fff;
}
</style>