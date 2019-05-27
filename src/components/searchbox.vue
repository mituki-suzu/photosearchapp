<template>
    <div id="searchbox">
        <!-- <input class="search" type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        {{msg}} -->
        <div> 
            F値：
            <input type="range" value="1" min="0" max="10" step="0.1" v-model="num" style="margin-top:50px">
            {{num}}
        </div>
        
        <div class="focal-length">
            <div v-for="(image,id) in images" :key="image.id" class="focal-length-radio">
            <label>
                <!-- 画像選択のラジオボタン -->
                <input type="radio" name="radio_image" :value="id" v-model="imgId" style="display:none; margin:0"><br>
                <p v-if="image.id==imgId" style="margin:0">
                    <img :src="image.imgSelect" class="focal-length-radio-img">
                </p>
                <p v-else  style="margin:0">
                    <img :src="image.imgNonSelect" class="focal-length-radio-img">
                </p>
            </label>
        </div>

        </div>
        
        <button class="search-button" @click="search(num, imgId)" >検索</button>
        <p>
            {{result}}
        </p>
    </div>
</template>

<script>
export default {
    data () {
        return {
            // msg: "",
            num: '0',
            images: [
                {id: 0, imgSelect: require('@/assets/30mmSelect.png'), imgNonSelect: require('@/assets/30mmNonSelect.png')},
                {id: 1, imgSelect: require('@/assets/50mmSelect.png'), imgNonSelect: require('@/assets/50mmNonSelect.png')},
                {id: 2, imgSelect: require('@/assets/75mmSelect.png'), imgNonSelect: require('@/assets/75mmNonSelect.png')},
            ],
            imgId: 0,
            result: "result",
        }
    },
    methods: {
        search (num, imgID) {
            // flicker apiで検索して結果を返す
            this.result = num + " : " + imgID
        },
    },
}
</script>

<style>
#searchbox{
    /* border: double 5px blue; */
    text-align: center;
}

.search{
    width: 50%;
}

.search-button{
    margin: auto;
}

/* クラス内一番最初のdiv要素に付加 */
    /* 親コンポーネントでマージン取る方向に転換 */
/* .focal-length div:first-of-type{
    margin-left: 10%;
} */

.focal-length{
    margin: 0 10%;
}

.focal-length-radio{
    width:20%;
    display: inline-block;
    margin-right: 10%;
}

.focal-length-radio:last-child{
    margin-right: 0;
}

.focal-length-radio-img{
    width:100%;
}
</style>
