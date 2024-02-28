

<template>
    <div class="container">
        <div class="min-h-[calc(100vh-160px)]">
            <div class="flex gap-x-5  py-4">
                <div class="w-[70%] border border-slate-400 p-4 rounded-lg">
                    <div v-if="loader" class="flex items-center justify-center h-full">
                       
                     
                        <i class="pi pi-spin pi-spinner text-[50px]"></i>
                    </div>
                    <div v-else class="flex flex-col">
                        <div>
                            <h2 class="font-semibold text-[30px] capitalize">{{ region }}</h2>
                            <p class="font-medium text-[15px]">
                                {{
                                    new Date(dayNames[0]?.dt * 1000).toLocaleDateString("en", {
                                    weekday: "long",
                                    })
                                }},

                                {{ 
                                    new Date(dayNames[0]?.dt * 1000).toLocaleString('en-US', {
                                        day: '2-digit',
                                    })
                                }}

                            </p>
                        </div>

                        <div class="flex items-center justify-between">
                            <div class="flex gap-x-4 text-blue-600 text-[100px] font-semibold">
                                <span class="font-bold">{{ temperature }}</span> <span>&deg; C</span>
                            </div>
                            <img :src="'https://openweathermap.org/img/wn/' + link + '@2x.png'" alt="weather" class="w-[250px] object-cover">
                        
                        </div>

                        
                            
                            <div class="grid grid-cols-4 gap-4">
                                <template v-for="(item, index) in dayNames" :key="index"> 
                                    <div class=" bg-white py-4 border border-gray-200 rounded-xl">
                                        <p class="text-center">
                                            {{
                                                new Date(item.dt * 1000).toLocaleDateString("en", {
                                                    weekday: "long",
                                                })
                                            }}
                                            ,
                                            <span>
                                                {{ 
                                                    new Date(item.dt * 1000).toLocaleString('en-US', {
                                                        day: '2-digit',
                                                    })
                                                 }}
                                            </span>
                                        </p>
                                        <img :src="'https://openweathermap.org/img/wn/' + item.weather[0].icon + '@2x.png'" alt="weather" class="w-[150px] object-cover mx-auto">
                                        
                                        <p class="flex items-center justify-center font-semibold">
                                            <span class="text-[16px]">{{ item.temp.day }}</span>

                                            <sup>&deg; C</sup>
                                        </p>
                                    </div>
                                </template>
                            </div>
                           
                        
                    </div>
                </div>
                <div class="w-[25%] bg-slate-200 py-4 px-2 rounded-lg">
                    <h2 class="mb-5 text-center font-bold text-xl">Regions</h2>

                    <ul class="flex flex-col gap-y-2 text-md cursor-pointer w-full">
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('karakalpakstan')">
                            <label for="tash" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Tashkent city</span>
                                <input id="tash" type="radio" name="r" checked>
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('karakalpakstan')">
                            <label for="kr" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Republic of Karakalpakstan</span>
                                <input id="kr" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('andijan')">
                            <label for="an" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Andijan</span>
                                <input id="an" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('bukhara')">
                            <label for="bk" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Bukhara</span>
                                <input id="bk" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('qarshi')">
                            <label for="kash" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Kashkadarya</span>
                                <input id="kash" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('jizzakh')">
                            <label for="jz" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Jizzakh</span>
                                <input id="jz" type="radio" name="r">
                            </label>
                        </li>
                        
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('navoi')">
                            <label for="nv" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Navoi</span>
                                <input id="nv" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('namangan')">
                            <label for="nm" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Namangan</span>
                                <input id="nm" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('samarkand')">
                            <label for="sm" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Samarkand</span>
                                <input id="sm" type="radio" name="r">
                            </label>
                        </li>

                        <li class="hover:bg-white p-2 rounded-md" @click="getName('sirdaryo')">
                            <label for="sir" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Sirdarya</span>
                                <input id="sir" type="radio" name="r">
                            </label>
                        </li>

                        <li class="hover:bg-white p-2 rounded-md" @click="getName('khujand')">
                            <label for="sur" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Surkhandarya</span>
                                <input id="sur" type="radio" name="r">
                            </label>
                        </li>
                       
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('fergana')">
                            <label for="fr" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Fergana</span>
                                <input id="fr" type="radio" name="r">
                            </label>
                        </li>
                        <li class="hover:bg-white p-2 rounded-md" @click="getName('urgench')">
                            <label for="kh" class="flex items-center justify-between w-full cursor-pointer">
                                <span>Khorezm</span>
                                <input id="kh" type="radio" name="r">
                            </label>
                        </li>
                        
                    </ul>
                </div>
            </div>
        </div>
    </div>
    
</template>

<script setup>
    import { ref, watch } from "vue";
    import axios from "axios";
    import { onMounted } from "vue";
    

    const link = ref('');
    const temperature = ref('');
    const dayNames = ref([]);
    const region = ref('Tashkent');
    const loader  = ref(false);
    const apiKey = "9dd86907fe501cec50da3d087e4e9dc0";
    
    const getName = (value) => {
        region.value = value;
    }
    const getData = async () => {
        
        const url = `https://api.openweathermap.org/data/2.5/weather?q=${region.value}&appid=${apiKey}`;
        try {
            const res = await axios(url);
            const data = res.data;
            const lat = data.coord.lat;
            const lon = data.coord.lon;
            getDatafor7days(lat, lon);
        } catch (error) {
            console.log(error);
        }
    };

    const getDatafor7days = async (lat, lon) => {
        loader.value = true
        let url = `https://api.openweathermap.org/data/2.8/onecall?lat=${lat}&lon=${lon}&units=metric&exclude=minutely,hourly,alerts&appid=${apiKey}`
        try {
            const res = await axios(url);
            const data = res.data;
            dayNames.value = data.daily;
            link.value = data.current.weather[0].icon;
            temperature.value = data.current.temp;
            loader.value = false;
        } catch (error) {
            console.log(error);
            loader.value = false
        }
    };

   

    onMounted(() => {
        getData();
    })

    watch(() => region.value, () => {
        getData();
    }); 
</script>

<style lang="scss" scoped>

</style>