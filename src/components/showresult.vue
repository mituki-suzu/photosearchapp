<template>
<!-- このコンポーネントでは検索結果を表示する -->
    <div>
        <p id="subtitle">お気に入りを撮りに出かけよう。</p>
        <expandimages v-bind:image-title="t" v-bind:image-url="a" v-bind:image-tag="b"></expandimages>

        <input id="keyword" type="text" placeholder="キーワードを入力して検索" v-model="keyword">
        <button id="keywordbutton" @click.prevent="search(1)">検索</button>
        <!-- {{searchValue}} -->
        <div id="showresult">
            <div v-if="loading" style="">
                <div id="loading" style="font-size:20px;">Loading...</div>
            </div>
            <p v-else class="result">
                <img :src="simage.url_n" v-for="simage in searchimages" :key="simage.id" @click="expandimg(simage.title, simage.url_n, simage.tags)">
            </p>  
        </div><link href="https://fonts.googleapis.com/css?family=Noto+Sans+JP&display=swap" rel="stylesheet">
    </div>
</template>

<script>
import expandimages from './expandimages'

import config from '../../config2';
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
            keyword: "",
            a: "none",
            b: "none",
            t: "none",
        }
    },
    methods: {
        expandimg(title, url, tags){
            this.t = title;
            this.a = url;
            this.b = tags;
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
                    per_page: 100,
                    media: 'photos',
                    // tag_mode:'all',
                    // 関連度の高い順
                    // sort: 'relevance'
                    // 人気の高い順
                    sort: 'interestingness-desc'
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
                    extras: 'url_n, tags',
                    page: 1,
                    format: 'json',
                    nojsoncallback: 1,
                    per_page: 100,
                    media: 'photos',
                    // tag_mode:'all',
                    // 関連度の高い順
                    // sort: 'relevance'
                    // 人気の高い順
                    sort: 'interestingness-desc'
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
#subtitle {
    color: #76727B;
    font-size: 7px;
    font-family: 'Noto Sans JP';
    display: inline-block;
    margin: 45px 0 0 10%;;
    width: 160px;
}

#keyword {
    float: right;
    width: 205px;
    height: 26px;
    margin: 36px 45px 40px 0;
    background-color: #F5F5FA;
    border: solid 1px #DADAE2;
    border-radius: 0 3px 3px 0;
    font-size: 8px;
    text-indent: 10px;
    color: #76727B;
}

#keywordbutton {
    float: right;
    margin: 36px 0 40px 0;
    width: 40px;
    height: 30px;
    background-color: #E14658;
    border: solid 1px #E14658;
    /* background-color: #313138; */
    /* border: solid 1px #4D4F60; */
    border-radius: 3px 0 0 3px;
    color: #fff;
    font-size: 9px;
}

#showresult {
    width: 90%;
    margin: 0 5%;
}

.result {
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

.result img {
    /* border: solid 1px red; */
    width: 90%;
    height: auto;
    margin-bottom: 10%;
    border-radius: 5px;
    filter: drop-shadow(0px 3px 3px rgba(0, 0, 0, 0.3));
}

.result img:hover {
    opacity: 0.6;
    /* transition-duration: 0.3s; */
    /* position:relative;
    top:0; right:0; bottom:0; left:0;
    border-radius:3px;
    z-index:2;
    box-shadow:inset 0 10px 3px rgba(0,0,0,0.5); */
}

</style>
