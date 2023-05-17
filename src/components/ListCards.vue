<script>
import Card from "@/components/Card.vue";

export default {
    components:{
        Card
    },
    props:{
        infoList:[]
    },
}

</script>

<template>
    <div v-for="(info) in infoList">
        <card
            :name="info.name"
            :condition="info.condition"
            :icon="info.icon"
            :temp-c="info.tempC"
            :precipitation="info.precipitation"
            :wind="info.wind"
            :feels-like="info.feelsLike"
            :uv="info.uv"
        ></card>
    </div>
</template>

<style scoped>

</style>