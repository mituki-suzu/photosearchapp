<template>
<!-- このコンポーネントでは検索結果を表示する -->
    <div>
        <expandimages id="sresult" v-bind:search-value=[a,b]></expandimages>

        <input id="keyword" type="text" placeholder="検索したいワードを入力してください" v-model="keyword">
        <button id="keywordbutton" @click.prevent="search(1)">検索</button>
        <!-- {{searchValue}} -->
        <div id="showresult">
            <p v-if="loading">
                Loading...
            </p>
            <p v-else class="result">
                <img :src="simage.url_n" v-for="simage in searchimages" :key="simage.id" @click="expandimg(simage.url_n, simage.tags)">
            </p>  
        </div>
        <!-- <p style="text-align:center;">今選択している画像のF値：{{result}}</p> -->
        <!-- <div id="result"  v-for="(image) in images" :key="image.id">
                <img :src="image.img" :alt="image.alt" @click="show(image.alt)">
        </div>  -->
    </div>
</template>

<script>
import expandimages from './expandimages'

import config from '../../config';
import axios from 'axios';

export default {
    // 親からsearchboxのデータを受け取る
    props: ["searchValue"],
    components: {
        expandimages,
    },
    data() {
        return{
            result:"test",
            loading: false,
            searchimages: [],
            keyword:"",
            test:" test ",
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
        }
    },
    methods: {
        expandimg(url, tags){
        },
        search(n) {
            this.loading = true;
            if(n == 0){
                this.fetchImages0()
                .then((response) => {
                    this.searchimages = response.data.photos.photo;
                    this.loading = false;
                })
            }else{
                this.fetchImages1()
                .then((response) => {
                    this.searchimages = response.data.photos.photo;
                    this.loading = false;
                })

            }
        },

        fetchImages0() {
            return axios({
                method: 'get',
                url: 'https://api.flickr.com/services/rest',
                params: {
                    method: 'flickr.photos.search',
                    api_key: config.api_key,
                    text: this.searchValue,
                    // tags: this.searchValue,
                    extras: 'url_n, owner_name, date_taken, views, tags',
                    page: 1,
                    format: 'json',
                    nojsoncallback: 1,
                    per_page: 16,
                    media: 'photos',
                    // tag_mode:'all',
                    sort: 'relevance'
                }
            })
        },

        fetchImages1() {
            return axios({
                method: 'get',
                url: 'https://api.flickr.com/services/rest',
                params: {
                    method: 'flickr.photos.search',
                    api_key: config.api_key,
                    text: this.keyword,
                    extras: 'url_n, owner_name, date_taken, views, tags',
                    page: 1,
                    format: 'json',
                    nojsoncallback: 1,
                    per_page: 16,
                    media: 'photos',
                    // tag_mode:'all',
                    sort: 'relevance'
                }
            })
        },
    },
    watch: {
        // 親からデータを受け取るたびに実行
        searchValue: function () {
            this.search(0)
        }
    },
}
</script>

<style>
#keyword{
    float: right;
    width: 205px;
    height: 25px;
    margin: 36px 45px 40px 0;
    background-color: #313138;
    border: solid 1px #4D4F60;
    border-radius: 3px;
    font-size: 8px;
    text-indent: 10px;
    color: #fff;
}

#keywordbutton{
    float: right;
    margin: 36px 0 40px 0;
    width: 40px;
    height: 30px;
    background-color: #218789;
    border: solid 1px #218789;
    /* background-color: #313138; */
    /* border: solid 1px #4D4F60; */
    border-radius: 3px;
    color: #fff;
    font-size: 9px;

}

#showresult{
    width: 80%;
    margin: 0 10%;
}

.result{
    display: inline-block;
    line-height: 0;
    margin-top: 0;
    -webkit-column-count: 4;
    -webkit-column-gap: 0;
    -moz-column-count: 4;
    -moz-column-gap: 0;
    column-count: 4;
    column-gap: 0;
}

.result img{
    /* border: solid 1px red; */
    width: 80%;
    height: auto;
    margin-bottom: 10%;
    border-radius: 5px;
    filter: drop-shadow(1px 1px 3px rgba(0,0,0,1.0));
}

.result img:hover{
    opacity: 0.6;
    transition-duration: 0.3s;
    /* position:relative;
    top:0; right:0; bottom:0; left:0;
    border-radius:3px;
    z-index:2;
    box-shadow:inset 0 10px 3px rgba(0,0,0,0.5); */
}

</style>
