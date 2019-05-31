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
            <div id="frange">
                <p id="focalnum">F : <input id="focalnuminput" v-model="num"></p>
                <div> 
                    <input type="range" value="1" min="0" max="10" step="0.1" v-model="num">
                </div>
            </div>
        </div>
        <div class="ac_menu">
            <input type="checkbox" id="Panel2" class="on-off" />
            <label for="Panel2">焦点距離</label>
            <div id='focusbase'>
                <select id="focus" size="1" name="sample">
                    <option value="">▽　指定なし</option>
                    <option value="14mm">14</option>
                    <option value="15mm">15</option>
                    <option value="17mm">17</option>
                    <option value="20mm">20</option>
                    <option value="22mm">22</option>
                    <option value="24mm">24</option>
                    <option value="28mm">28</option>
                    <option value="32mm">32</option>
                    <option value="35mm">35</option>
                    <option value="40mm">40</option>
                    <option value="45mm">45</option>
                    <option value="50mm">50</option>
                    <option value="60mm">60</option>
                    <option value="65mm">65</option>
                    <option value="70mm">70</option>
                    <option value="85mm">85</option>
                    <option value="90mm">90</option>
                    <option value="105mm">105</option>
                    <option value="135mm">135</option>
                    <option value="180mm">180</option>
                    <option value="200mm">200</option>
                    <option value="300mm">300</option>
                    <option value="400mm">400</option>
                    <option value="500mm">500</option>
                    <option value="600mm">600</option>
                    <option value="800mm">800</option>
                </select>
                <p>mm</p>
            </div>
        </div>
        <div class="ac_menu">
            <input type="checkbox" id="Panel3" class="on-off" />
            <label for="Panel3">カテゴリ</label>
            <div id="check">
                <p>
                <input id="box1" type="checkbox" value="1"/>
                    風景<br>
                <input id="box1" type="checkbox" value="2"/>
                    人物<br>
                <input id="box1" type="checkbox" value="2"/>
                    ポートレート<br>
                </p>
            </div>
        </div>
        <div style="text-align: center;">
            <button class="search-button" @click.prevent="updated" >検索</button>
        </div>
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
    font-size: 18px;
    margin: 34px 0 0 45px;
    font-family: 'Impact';
}

#subtitle{
    color: white;
    font-size: 7px;
    margin: 9px 0 30px 45px;
    font-family: 'Pro"Hiragino Kaku Gothic ProW4'
}

input[type=range] {
    -webkit-appearance: none;
    margin: 33px 0 0 45px;
    width: 175px;
    background: #393a45;
}

input[type=range]:focus {
    outline: none;
}

/* WebKit・Blinkの溝のスタイル */
input[type=range]::-webkit-slider-runnable-track {
    width: 17vw;
    height: 0.5vw;
    cursor: pointer;
    background: linear-gradient(90deg, #19696A, #238F91);
    border-radius: 5px;
}
/* WebKit・Blinkのつまみのスタイル */
input[type=range]::-webkit-slider-thumb {
    box-shadow: 1px 1px 1px #fff, 0px 0px 1px #fff;
    height: 15px;
    width: 15px;
    border-radius: 50%;
    background: #fff;
    cursor: pointer;
    -webkit-appearance: none;
    /*つまみの縦位置調整 */
    margin-top: -5px;
}

/* WebKit・Blinkのfocus時のスタイル */
input[type=range]:focus::-webkit-slider-runnable-track {
    background: linear-gradient(90deg, #19696A, #238F91);
}

.search-button{
    width: 110px;
    height: 30px;
    margin: 20px 0 0 0;
    background-color: #218789;
    border-style: none;
    border-radius: 30px;
    color: #fff;
    font-size: 9px;
    font-family: Noto Sans CJK JP;
}

#focalnum{
    margin: 14px 0 0 45px;
    color: #fff;
    font-size: calc(15% + 0.5vw);
}

#focalnuminput{
    width: 65px;
    color: white;
    background-color:#2E2E34;
    font-size: calc(30% + 0.5vw); 
    text-indent: 5px;
    border-style: none;
    border-bottom: solid #50525D 1px;
}

/* 焦点距離 */
#focusbase p{
    float: left;
    font-family: 'Noto Sans CJK JP';
    font-size: calc(15% + 0.5vw);
    color: #fff;
    margin: 18px 0 0 2px; 
}

#focus{
    float: left;
    margin: 14px 0 0 45px; 
    width: 6.5vw;
    /* border: solid #393a45 1px; */
    border-style: none;
    border-bottom: solid #50525D 1px;
    outline:none;
    text-indent: 0.01px;
    text-overflow: '';
    background: none transparent;
    vertical-align: middle;
    font-size: calc(15% + 0.5vw);
    color: #fff;
    -webkit-appearance: button;
    -moz-appearance: button;
    appearance: button;
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
    font-size:  10px;
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

#frange{
    padding: 0;
}

select option{
    /* background-color: #fff; */
    color: #333;
}
select::-ms-expand {
    display: none;
}
select:-moz-focusring { 
    color: transparent; 
    text-shadow: 0 0 0 #828c9a;
}

#check {
    color: #fff;
}


/* ゴミ */

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
