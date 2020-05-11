<template>
    <div id="carousel" class="container" :style="containerStyle" @mouseout="handleLoop" @mouseover="clearLoop">
        <transition-group tag="ul" class='slide-ul' :name="transType">
            <li v-for="(item,index) in slides" :key="item.id" v-show="index===nowIndex">
                <img class="items-show" v-if="isShow" :src="item.src" :alt="item.title">
            </li>
        </transition-group>
        <ul class="direction" v-if="btnStyle !== 'dot'">
            <li @click="move(-1)">
                <svg class="icon" width="25px" height="25.00px" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"><path fill="#ffffff" d="M481.233 904c8.189 0 16.379-3.124 22.628-9.372 12.496-12.497 12.496-32.759 0-45.256L166.488 512l337.373-337.373c12.496-12.497 12.496-32.758 0-45.255-12.498-12.497-32.758-12.497-45.256 0l-360 360c-12.496 12.497-12.496 32.758 0 45.255l360 360c6.249 6.249 14.439 9.373 22.628 9.373z"  /></svg>
            </li>
            <li @click="move(1)">
                <svg class="icon" width="25px" height="25.00px" viewBox="0 0 1024 1024" version="1.1" xmlns="http://www.w3.org/2000/svg"><path fill="#ffffff" d="M557.179 904c-8.189 0-16.379-3.124-22.628-9.372-12.496-12.497-12.496-32.759 0-45.256L871.924 512 534.551 174.627c-12.496-12.497-12.496-32.758 0-45.255 12.498-12.497 32.758-12.497 45.256 0l360 360c12.496 12.497 12.496 32.758 0 45.255l-360 360c-6.249 6.249-14.439 9.373-22.628 9.373z"  /></svg>
            </li>
        </ul>
        <div class="carousel-items" :style="carouselItemsT" v-if="btnStyle !== 'side'">
            <span v-for="(item,index) in slides.length" :class="{'active':index===nowIndex}"
                  @mouseover="change(index)"></span>
        </div>
    </div>
</template>

<script>
export default {
    name: 'carousel',
    props: {
        options: {
            type: Object,
            default () {
                return {
                    interval: 4000,
                    width: 600,
                    height: 400
                }
            }
        },
        btnStyle:{
            String,
            default () {
                return 'normal'
            }
        },
        slides: Array,
    },
    data () {
        return {
            containerStyle: {}, // 容器大小设置
            carouselItemsT:{}, // 底部按钮位置
            nowIndex: 0, // 当前图片索引
            isShow: true,
            transType: 'transRight' // 过渡方式
        }
    },
    mounted () {
        this.handleLoop()
    },
    // 初始化设置
    created () {
        this.options.interval =  this.options.interval || 4000
        let {width,height} = this.options
        width = width || 600
        height = height || 400
        this.containerStyle = {
            width: width+'px',
            height: height+'px'
        }
        this.carouselItemsT = {
            top: height*0.9+'px'
        }
    },
    methods: {
        // 循环播放
        handleLoop () {
            this.transType = 'transRight'
            console.log('aa')
            this.clock = setInterval(() => {
                this.nowIndex++
                if (this.nowIndex === this.slides.length) this.nowIndex = 0
            }, this.options.interval)
        },
        // 停止播放
        clearLoop () {
            console.log('bb')
            clearInterval(this.clock)
        },
        // 点选择
        change (index) {
            this.transType = index < this.nowIndex? 'left':'transRight'
            this.nowIndex = index
        },
        // 左右按钮选择
        move(num){
            this.transType = num < 0? 'left':'transRight'
            if (this.nowIndex+num < 0) this.nowIndex = this.slides.length - 1
            else if (this.nowIndex+num === this.slides.length) this.nowIndex = 0
            else this.nowIndex += num
        }
    }
}
</script>

<style scoped>
.container {
    position: relative;
    overflow: hidden;
}

.slide-ul li {
    position: absolute;
    width: 100%;
    height: 100%;
    list-style-type: none;
}

.slide-ul li img {
    width: 100%;
    height: 100%;
}

.carousel-items {
    position: absolute;
    z-index: 10;
    width: 100%;
    margin: 0 auto;
    text-align: center;
    font-size: 0;
}

.carousel-items span {
    display: inline-block;
    height: 6px;
    width: 30px;
    margin: 0 3px;
    background-color: #b2b2b2;
    cursor: pointer;
}

.carousel-items span:hover {
    background-color: #474747;
}
.direction{
    position: absolute;
    width: 100%;
    top: 0;bottom: 0;
    margin: auto;
    display: flex;
    align-items: center;
    justify-content: space-between;
}
.direction li{
    list-style: none;
}
.icon{
    background: rgba(178, 178, 178, 0.51);
    width: 40px;
    height: 40px;
    border-radius: 100%;
    z-index: 100;
}
.left-enter{
    transform: translateX(-100%);
    transition: all 0.5s ease;
}
.left-enter-to{
    transition: all 0.5s ease;
}
.left-leave-active {
    transition: all 0.5s ease;
    transform: translateX(100%)
}
.transRight-enter {
    transform: translateX(100%)
}

.transRight-enter-to {
    transition: all 0.5s ease;
}

.transRight-leave-active {
    transition: all 0.5s ease;
    transform: translateX(-100%)
}

</style>
