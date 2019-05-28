<template>
    <div id="searchbox">
        <!-- <input class="search" type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        {{msg}} -->
        F値 : {{num}}
        <div style="text-align: center"> 
            <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
        </div>

        <select size="1" name="sample">
            <option value="14mm">14mm</option>
            <option value="15mm">15mm</option>
            <option value="17mm">17mm</option>
            <option value="20mm">20mm</option>
            <option value="22mm">22mm</option>
            <option value="24mm">24mm</option>
            <option value="28mm">28mm</option>
            <option value="32mm">32mm</option>
            <option value="35mm">35mm</option>
            <option value="40mm">40mm</option>
            <option value="45mm">45mm</option>
            <option value="50mm">50mm</option>
            <option value="60mm">60mm</option>
            <option value="65mm">65mm</option>
            <option value="70mm">70mm</option>
            <option value="85mm">85mm</option>
            <option value="90mm">90mm</option>
            <option value="105mm">105mm</option>
            <option value="135mm">135mm</option>
            <option value="180mm">180mm</option>
            <option value="200mm">200mm</option>
            <option value="300mm">300mm</option>
            <option value="400mm">400mm</option>
            <option value="500mm">500mm</option>
            <option value="600mm">600mm</option>
            <option value="800mm">800mm</option>
        </select>

        <!-- 画像選択のラジオボタン -->     
        <!-- <div class="focal-length">
            <div v-for="(image,id) in images" :key="image.id" class="focal-length-radio">
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
            // images: [
            //     {id: 0, imgSelect: require('@/assets/30mmSelect.png'), imgNonSelect: require('@/assets/30mmNonSelect.png')},
            //     {id: 1, imgSelect: require('@/assets/50mmSelect.png'), imgNonSelect: require('@/assets/50mmNonSelect.png')},
            //     {id: 2, imgSelect: require('@/assets/75mmSelect.png'), imgNonSelect: require('@/assets/75mmNonSelect.png')},
            // ],
            // imgId: 0,
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

input[type=range] {
    -webkit-appearance: none;
    margin: 0;
    width: 80%;
    background: #8bc3f3;
}
input[type=range]:focus {
    outline: none;
}

/* WebKit・Blinkの溝のスタイル */
input[type=range]::-webkit-slider-runnable-track {
  width: 100%;
  height: 6px;
  cursor: pointer;
  background: #66a4f5;
  border-radius: 5px;
}
/* WebKit・Blinkのつまみのスタイル */
input[type=range]::-webkit-slider-thumb {
  box-shadow: 1px 1px 1px #1453a7, 0px 0px 1px #1453a7;
  height: 15px;
  width: 15px;
  border-radius: 50%;
  background: #418df0;
  cursor: pointer;
  -webkit-appearance: none;
  /*つまみの縦位置調整 */
  margin-top: -5px;
}

/* WebKit・Blinkのfocus時のスタイル */
input[type=range]:focus::-webkit-slider-runnable-track {
  background: #66a4f5;
}


#searchbox{
    /* border: double 5px blue; */
    /* text-align: center; */
}

/* .search{
    width: 50%;
} */

.search-button{
    margin-right: 10%;
    float: right;
}

/* クラス内一番最初のdiv要素に付加 */
    /* 親コンポーネントでマージン取る方向に転換 */
/* .focal-length div:first-of-type{
    margin-left: 10%;
} */

.focal-length{
    margin: 0 10%;
}

/* .focal-length-radio{
    width:20%;
    display: inline-block;
    margin-right: 10%;
}

.focal-length-radio:last-child{
    margin-right: 0;
} */

.focal-length-radio-img{
    width:100%;
}
</style>
