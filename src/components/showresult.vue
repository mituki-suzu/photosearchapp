<template>
<!-- このコンポーネントでは検索結果を表示する -->
    <div>
        {{searchValue}}
        <div id="showresult">
            <p v-if="loading">
                Loading...
            </p>
            <p v-else class="result" v-for="simage in searchimages" :key="simage.id">
                <img :src="simage.url_n">
            </p>  
        </div>
        <p style="text-align:center;">今選択している画像のF値：{{result}}</p>
        <div id="showresult">
            <p class="result" v-for="(image) in images" :key="image.id">
                <img :src="image.img" :alt="image.alt" @click="show(image.alt)">
            </p>
        </div> 
    </div>
</template>

<script>
import config from '../../config';
import axios from 'axios';

export default {
    // 親からsearchboxのデータを受け取る
    props: ["searchValue"],
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
            loading: false,
            searchimages: [],
        }
    },
    methods: {
        search() {
            this.loading = true;
            this.fetchImages()
            .then((response) => {
                this.searchimages = response.data.photos.photo;
                this.loading = false;
            })
        },

        fetchImages() {
            return axios({
                method: 'get',
                url: 'https://api.flickr.com/services/rest',
                params: {
                    method: 'flickr.photos.search',
                    api_key: config.api_key,
                    text: this.searchValue,
                    // tags: this.searchValue,
                    extras: 'url_n, owner_name, date_taken, views',
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
            this.search()
        }
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
