<template>
    <div id="searchbox">
        <p id="title">Torumo</p>
        <p id="subtitle">お気に入りを撮りに出かけよう</p>
        <!-- <input class="search" type="text" placeholder="検索したいワードを入力してください" v-model="msg">
        {{msg}} -->
        <!-- F値 : {{num}}
        <div> 
            <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
        </div> -->
    
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

        <div class="ac_menu">
            <input type="checkbox" id="Panel1" class="on-off" />
            <label for="Panel1">絞り値</label>
            <div>
                F値 : {{num}}
                <div> 
                    <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
                </div>
            </div>
        </div>
        <div class="ac_menu">
            <input type="checkbox" id="Panel2" class="on-off" />
            <label for="Panel2">焦点距離</label>
            <div>
                <select id="focus" size="1" name="sample">
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
            </div>
        </div>
        <div class="ac_menu">
            <input type="checkbox" id="Panel3" class="on-off" />
            <label for="Panel3">カテゴリ</label>
            <div>
                F値 : {{num}}
                <div> 
                    <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
                </div>
            </div>
        </div>

        <button class="search-button" @click.prevent="updated" >検索</button>
        </div>
</template>

<script>
import config from '../../config';
import axios from 'axios';

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
        }
    },
    methods: {
        //showresultにデータを送るために親にデータを送信
        updated() {
            // this.$emit('on-child-updated', "f"+ this.num);
            this.$emit('on-child-updated', "f"+ this.num + " " + document.getElementById('focus').value);
            // タグの時はカンマ
            // this.$emit('on-child-updated', "f"+ this.num + "," + document.getElementById('focus').value);
        },
    }
}
</script>

<style>
#title{
    color: white;
    font-size: 1.8vw;
    padding: 5% 18% 0 18%;
    margin-bottom: 0;
    font-family: 'Impact';
}

#subtitle{
    color: white;
    font-size: 0.7vw;
    padding: 0% 18%;
    margin-top: 5px;
    font-family: 'Pro"Hiragino Kaku Gothic ProW4'
}

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

.ac_menu{
  width: 100%;
}

/* メニューの部分 */
.ac_menu label{
    background: #393a45;
    color: #fff;
    display: block;
    margin: 0;
    border-top: solid 1px #51525C; 
    border-bottom: solid 1px #51525C; 
    cursor:pointer;
}
.ac_menu input[type="checkbox"].on-off{
    display: none;
}

/* コンテンツの部分 */
.ac_menu div{
    -webkit-transition: all 0.5s;
    -moz-transition: all 0.5s;
    -ms-transition: all 0.5s;
    -o-transition: all 0.5s;
    transition: all 0.5s;
    margin: 0;
    padding: 0 10px;
    list-style: none;
	background: #2e2e34;
}
.ac_menu input[type="checkbox"].on-off ~ div{
    height: 0;
    overflow: hidden;
}
.ac_menu input[type="checkbox"].on-off:checked ~ div{
    height: 100px;
}

.ac_menu label {
	font-family: 'Noto Sans CJK JP';
    font-size:  1.0vw;
	line-height: 3;
	position: relative;
	display: block;
    padding-left: 18%;
	cursor: pointer;
	background: #393a45;
    border-top: solid 1px #51525C; 
    border-bottom: solid 1px #51525C; 
}

/* Icon */
.ac_menu label::after {
	line-height: 3;
	position: absolute;
	top: 0;
	right: 0;
	display: block;
	width: 3em;
	height: 3em;
	-webkit-transition: all 0.35s;
	transition: all 0.35s;
	text-align: center;
}
.ac_menu input[type=checkbox] ~ label::after {
	content: '▲';
}
.ac_menu input[type=checkbox]:checked ~ label::after {
	transform: rotateX(180deg);
}
</style>
