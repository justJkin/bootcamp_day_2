<template>
    <div>
        <button @click="pobierzWpisy">odswiez</button>
        elo 
        {{ wpisy }}
        <input v-model="nowyBlog" type="text">
        <button @click="dodajWpis">dodaj</button>
    </div>
</template>

<script>
import { day_2_backend } from 'declarations/day_2_backend/index';
    export default {
        data() {
            return {
                wpisy:[],
                nowyBlog: "" , 
            }
        },
        methods: {
            async pobierzWpisy(){
                this.wpisy = await day_2_backend.oczytaj_wpisy();
            },
            async dodajWpis(){
               await day_2_backend.dodaj_wpis(this.nowyBlog);
            }
        },
    }
</script>