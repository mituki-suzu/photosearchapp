<template>
    <transition>
        <div v-if="expand" class="image-table">
            <div id="table-left">
                <p id="image-title">
                    {{ imageTitle }}
                </p>
                <p id="image-url">
                    URL : {{ imageUrl }}
                </p>
                <p id="square">今後カメラ情報を表示</p>
                <!-- forでタグごとに表示 -->
                <div v-if="imageTag != ''" id="tag-box">
                    <button id="image-tag" v-for="tag in imageTag.split(' ')" :key="tag.id">
                        {{ tag }}
                    </button>
                </div>
                <div v-else id="tag-box">
                    <button id="image-tag">
                        タグ無し
                    </button>
                </div>
            </div>
            <div id="table-right">
                <button class="close-button" @click="close()" style="width: 0; padding: 0; border: none;"><img src="../assets/cross.svg"></button>
                <img :src="imageUrl">
            </div>
        </div>
    </transition>
</template>

<script>
export default {
    //親からURLとタグを受け取る
    props:[
        "imageTitle",
        "imageUrl",
        "imageTag",
        "imageId",
    ],
    data(){
        return{
            expand : false,
        }
    },
    methods:{
        close(){
            this.expand = false;
        },
    },
    watch: {
        // 親からデータを受け取るたびに実行
        imageUrl: function () {
            this.expand = true;            
        }
    },
}
</script>

<style>
#square {
    width:80%;
    height: 175px;
    background-color: rgba(100, 97, 97, 0.7);
    font-family: 'Noto Sans JP';
    font-size: 12px; 
    vertical-align: middle;
    margin: 0 0 20px 10%; 
}

#table-left {
    /* display: inline-block; */
    width: 40%;
    margin: 0;
    float: left;
    text-align: center;
}

#table-right {
    /* display: inline-block; */
    width: 60%;
    height: 100%;
    margin: 0;
    float: left;
    text-align: center;
}
.close-button {
    display: block;
    float: right;
    margin: 30px 80px 0 80vw;
}

.image-table {
    position: fixed;
    z-index: 2;
    top: 0;
    left: 0;
    width: 100vw;
    height: 100vh;
    background-color: rgba(0, 0, 0, .7);
    display: table;
    /* transition: opacity 1.0s ease; */
    color: white;
    text-align: center;
}

.image-table img {
    height: 60%;
    margin-top: 15px;
}

#image-title {
    font-family: 'Noto Sans JP';
    font-size: 18px; 
    margin: 72px 0 20px 0;
    text-align: left;
    margin-left: 10%;
}

#image-url {
    font-family: 'Noto Sans JP';
    font-size: 11px; 
    text-align: left;
    margin: 0 0 20px 10%;
}

#tag-box {
    text-align: left;
    width: 80%;
    margin: 0 auto;
    height:70px;
    overflow: hidden;
}

#image-tag {
    width: auto;
    height: 30px;
    border: solid 1px #fff;
    background-color: rgba(0, 0, 0, 0);
    color: #fff;
    border-radius: 5px;
    padding: 0 10px;
    margin: 0 10px 5px 0;
    font-size: 10px;
}
</style>


