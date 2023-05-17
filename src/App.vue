<script>
import ListCards from "@/components/ListCards.vue";
import axios from "axios";

export default {
    components:{
        ListCards
    },
    data(){
        return{
            weatherList:[]
        }
    },
    mounted: function(){

        let items = [
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=San Jose, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Heredia, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Alajuela, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Cartago, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Limon, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Guanacaste, Costa Rica&aqi=no',
            'https://api.weatherapi.com/v1/current.json?key=f8b800642fcd4e4d886202720231305&q=Puntarenas, Costa Rica&aqi=no'
        ];

        Promise.all(items.map(axios.get))
            .then(weatherList => {
                weatherList.forEach( result => {
                    this.weatherList.push({
                        name:result.data.location.name,
                        condition:result.data.current.condition.text,
                        icon: result.data.current.condition.icon,
                        tempC: result.data.current.temp_c,
                        precipitation: result.data.current.humidity,
                        wind: result.data.current.wind_kph,
                        feelsLike: result.data.current.feelslike_c,
                        uv: result.data.current.uv
                    })
                });
            });

    }
}

</script>

<template>
    <div class="container">
        <h1 class="ff-montserrat fw-semi-bold m-b-0 font-size-55">Weather</h1>
        <h2 class="ff-montserrat fw-light m-t-0 font-size-39">Costa Rica</h2>
        <list-cards :info-list="weatherList" ></list-cards>
    </div>
</template>

<style scoped>

</style>