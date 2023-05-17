<script>

export default {
    props:{
        name:{
            type: String,
            default: "N/A Name"
        },
        condition:{
            type: String,
            default: "N/A Condition"
        },
        icon:{
            type: String,
            default: "N/A Icon"
        },
        tempC:{
            type: String,
            default: "N/A TempC"
        },
        precipitation:{
            type: String,
            default: "N/A Precipitation"
        },
        wind:{
            type: String,
            default: "N/A Wind"
        },
        feelsLike:{
            type: String,
            default: "N/A Feels like"
        },
        uv:{
            type: String,
            default: "N/A UV"
        },
    },
    data: function () {


        // CARD CLR TEMP
        let clrTemp = this.tempC;
        let newClrTemp;

        if (clrTemp <= 15) {
            this.newClrTemp = ' bg-10-15 '
        }else if(clrTemp > 15 && clrTemp <=20){
            this.newClrTemp  = ' bg-16-20 '
        }else if(clrTemp > 20 && clrTemp <=26){
            this.newClrTemp = ' bg-21-26 '
        }else if(clrTemp > 26 && clrTemp <=31){
            this.newClrTemp = ' bg-27-31 '
        }else if(clrTemp > 31 && clrTemp <=37){
            this.newClrTemp =  ' bg-32-37 '
        }else if(clrTemp > 37){
            this.newClrTemp =  ' bg-38 '
        }


        // UV
        let uv = this.uv
        let newUV;
        if (uv <=2){
            this.newUV = 'Low'
        }else if(uv > 2 && uv <=5){
            this.newUV = 'Moderate'
        }else if(uv > 5 && uv <=7){
            this.newUV =  'High'
        }else if(uv > 7 && uv <=10){
            this.newUV =  'Very High'
        }else if(uv > 10){
            this.newUV =  'Extreme'
        }

        return{
            newClrTemp: this.newClrTemp,
            newUV: this.newUV
        }
    }
}

</script>

<template>
    <div class="card br-10 m-t-30 ff-sf-ui-display"
         :class="newClrTemp"
    >
        <div class="card-head m-l-20 m-r-20">
            <div class="text-align-start">
                <h3 class="m-b-0 fw-bold">{{name}}</h3>
                <p class="font-size-14">{{condition}}</p>
            </div>
            <div class="m-t-20">
                <img :src="'https:' + icon" alt="sun and clouds">
            </div>
        </div>
        <div class="card-body text-align-start m-l-20 m-r-20 p-b-10 m-b-20">
            <p class="fw-light m-t-0 font-size-14">
                <span class="font-size-30 fw-semi-bold m-r-20">{{tempC}}C°</span>
                <span class="font-size-16 m-r-15"><i class="fa-solid fa-umbrella m-r-5"></i> {{precipitation}}%</span>
                <span class="font-size-16"><i class="fa-solid fa-wind m-r-10"></i>{{wind}} kph</span>
                <br>
                Feels Like {{feelsLike}}C°
                <br>
                UV Index: {{newUV}}
            </p>
        </div>
    </div>
</template>
<style scoped>

.space{
}

.card-head{
    display: flex;
    justify-content: space-between;
}
img{
    width: 20vw;
}
</style>