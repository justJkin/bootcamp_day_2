<template>
    <div>
        <h2 class="text-blue-600">Wpisy na bloga: </h2>
        <div class="w-100 flex flex-row-reverse">
            <button @click="pobierzWpisy" class="bg-blue-600 rounded text-white p-4">odswiez</button>
        </div>
        <div class="grid mx-6 gap-4 my-4"> 
            <div v-for="(wpis, index) in wpisy" class="drop-shadow-xl bg-stone-300 p-4">
                <p>id: {{ index }}</p>
                <p>{{ wpis }}</p>
            </div>
        </div>
        <div class="flex justify-content-center flex-col">     
            <input v-model="nowyBlog" class="border-2 border-blue-600 p-4 " type="text">
            <button class="bg-blue-600 rounded text-white p-4" @click="dodajWpis">dodaj</button>
        </div>    
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

        async mounted(){
            this.pobierzWpisy;
        }
    }
</script>