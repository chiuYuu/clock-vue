<script>
import Clock from '@/components/Clock.vue';

export default {
    components: {
        Clock,
    },

    data() {
        return {
            regions: [
                { name: '墨西哥', timeZone: 'America/Mexico_City' },
                { name: '加拿大', timeZone: 'America/Toronto' },
                { name: '海地', timeZone: 'America/Port-au-Prince' },
                { name: '阿根廷', timeZone: 'America/Argentina/Buenos_Aires' },
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