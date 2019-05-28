<template>
<!-- このコンポーネントでは検索結果を表示する -->
    
    <div>
        <p style="text-align:center;">今選択している画像のF値：{{result}}</p>
        <div id="showresult">
            <p class="result" v-for="(image) in images" :key="image.id">
                <img :src="image.img" :alt="image.alt" @click="show(image.alt)">
            </p>
        </div> 
    </div>
</template>

<script>
export default {
    data() {
        return{
            result:"test",
            images: [
                {id: 0, img: require('@/assets/exsampleImages/im11.jpg'), alt:"f1.1"},
                {id: 1, img: require('@/assets/exsampleImages/im12.jpg'), alt:"f1.2"},
                {id: 2, img: require('@/assets/exsampleImages/im13.jpg'), alt:"f1.3"},
                {id: 3, img: require('@/assets/exsampleImages/im14.jpg'), alt:"f1.4"},
                {id: 4, img: require('@/assets/exsampleImages/im15.jpg'), alt:"f1.5"},
                {id: 5, img: require('@/assets/exsampleImages/im16.jpg'), alt:"f1.6"},
                {id: 6, img: require('@/assets/exsampleImages/im17.jpg'), alt:"f1.7"},
                {id: 7, img: require('@/assets/exsampleImages/im18.jpg'), alt:"f1.8"},
            ],
        }
    },
    methods: {
        show(alt) {
            // flicker apiで検索して結果を返す
            this.result = alt
        },
    },
}
</script>

<style>
#showresult{
    width: 80%;
    margin: 0 10%;
}

.result{
    width: 20%;
    /* border: solid 1px red; */
    display: inline-block;
    margin-right: 6%;
}

.result:nth-child(4n){
    margin-right: 0;
}

.result img{
    width: 15vw;
    height: 10vw;
    object-fit: cover;
}
</style>
