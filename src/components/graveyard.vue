<template>
    <div>
        <!-- <p v-if="msg.length > 0">
        {{msg}}
        </p> -->
        <!-- <p v-else>
            no text
        </p> -->
        <!-- <input type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        <button @click="search()">検索</button> -->

        <!-- <p style="text-align:center;">今選択している画像のF値：{{result}}</p> -->

        <!-- <div id="result"  v-for="(image) in images" :key="image.id">
                <img :src="image.img" :alt="image.alt" @click="show(image.alt)">
        </div>  -->

        <!-- <input class="search" type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        {{msg}} -->
        <!-- F値 : {{num}}
        <div> 
            <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
        </div> -->
    
        <!-- 画像選択のラジオボタン -->     
        <!-- <div class="focal-length">
            <div v-for="(image,id) in images2" :key="image.id" class="focal-length-radio">
            <label>
               
                <input type="radio" name="radio_image" :value="id" v-model="imgId" style="display:none; margin:0"><br>
                <p v-if="image.id==imgId" style="margin:0">
                    <img :src="image.imgSelect" class="focal-length-radio-img">
                </p>
                <p v-else  style="margin:0">
                    <img :src="image.imgNonSelect" class="focal-length-radio-img">
                </p>
            </label>
            </div>
        </div> -->
    </div>
</template>

<script>
export default {
    data () {
        return {
            msg:"",
            // images: [
            //     {id: 0, img: require('@/assets/exsampleImages/im11.jpg'), alt:"f1.1"},
            //     {id: 1, img: require('@/assets/exsampleImages/im12.jpg'), alt:"f1.2"},
            //     {id: 2, img: require('@/assets/exsampleImages/im13.jpg'), alt:"f1.3"},
            //     {id: 3, img: require('@/assets/exsampleImages/im14.jpg'), alt:"f1.4"},
            //     {id: 4, img: require('@/assets/exsampleImages/im15.jpg'), alt:"f1.5"},
            //     {id: 5, img: require('@/assets/exsampleImages/im16.jpg'), alt:"f1.6"},
            //     {id: 6, img: require('@/assets/exsampleImages/im17.jpg'), alt:"f1.7"},
            //     {id: 7, img: require('@/assets/exsampleImages/im18.jpg'), alt:"f1.8"},
            // ],
            // images2: [
            //     {id: 0, imgSelect: require('@/assets/30mmSelect.png'), imgNonSelect: require('@/assets/30mmNonSelect.png')},
            //     {id: 1, imgSelect: require('@/assets/50mmSelect.png'), imgNonSelect: require('@/assets/50mmNonSelect.png')},
            //     {id: 2, imgSelect: require('@/assets/75mmSelect.png'), imgNonSelect: require('@/assets/75mmNonSelect.png')},
            // ],
            // imgId: 0,
        }
    },
    methods:{
        search(){
        },
    }
}
</script>

<style>

/* #searchbox{
    border: double 5px blue;
    text-align: center;
} */

/* クラス内一番最初のdiv要素に付加 */
    /* 親コンポーネントでマージン取る方向に転換 */
/* .focal-length div:first-of-type{
    margin-left: 10%;
} */

/* .focal-length{
    margin: 0 10%;
} */

/* .focal-length-radio{
    width:20%;
    display: inline-block;
    margin-right: 10%;
}

.focal-length-radio:last-child{
    margin-right: 0;
} */
/* 
.focal-length-radio-img{
    width:100%;
} */
</style>

