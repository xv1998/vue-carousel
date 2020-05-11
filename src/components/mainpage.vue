<template>
    <div id="main" class="main">
        <carousel class="carousel" :slides="slidesArray" :options="options" :btnStyle="btnStyle"></carousel>
    </div>
</template>

<script>
/* eslint-disable */
import carousel from './common/carousel.vue'

export default {
    name: 'mainPage',
    components: {
        carousel,
    },
    data () {
        return {
            slidesArray:[{
               id:0,
               src: require('@/assets/1.png'),
                title:'background'
            },{
                id:1,
                src: require('@/assets/2.png'),
                title:'logo'
            },{
                id:2,
                src: require('@/assets/3.png'),
                title:'logo'
            },{
                id:3,
                src: require('@/assets/logo.png'),
                title:'logo'
            }],
            options:{
                width:700,
                height:500,
                interval:1000
            },
            btnStyle:'side'
        }
    },
    methods: {

    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>


</style>
