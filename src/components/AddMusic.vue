<script setup lang="ts">
import { getCurrentInstance } from 'vue'
const { proxy } = getCurrentInstance()
import { useMusicStore } from '@/stores/music'
import { storeToRefs } from 'pinia'
import Music from '@/models/music';
const store = useMusicStore()
var musicInfo:Music = storeToRefs(store).editMusicDetail
const submit = () => {
    proxy.$emit('submit')
}
const cancel = () => {
    proxy.$emit('cancel')
}
</script>
<template>
    <div id="main">
        <table>
            <tr>
                <td width="100px">歌曲标题</td>
                <td width="200px"><input v-model="musicInfo.musicName" type="text"></td>
            </tr>
            <tr>
                <td>歌手</td>
                <td><input v-model="musicInfo.artistName" type="text"></td>
            </tr>
            <tr>
                <td>专辑</td>
                <td><input v-model="musicInfo.albumName" type="text"></td>
            </tr>
        </table>
        <button id="submit" @click="submit">提交</button>
        <button id="cancel" @click="cancel">取消</button>
    </div>
</template>
<style scoped>
#main {
    width: 600px;
    height: 400px;
    background: rgba(255, 255, 255, 0.1);
    backdrop-filter: blur(15px);
    position: absolute;
    left: 0;
    top: 0;
    right: 0;
    bottom: 0;
    margin: auto;
    z-index: 18;
    border-radius: 50px;
    box-shadow: 2px 2px 10px 1px rgba(0, 0, 0, 0.2);
    color: #134991;
}

tr {
    height: 70px;
}

table {
    width: 500px;
    margin: 55px auto;
    font-size: 21px;

}

#fileUpload {
    width: 170px;
}

button {
    width: 150px;
    height: 40px;
    position: absolute;
    bottom: 50px;
    left: calc(50% - 100px);
    border-radius: 30px;
    background-color: white;
    border: none;
    box-shadow: 2px 2px 10px 1px rgba(0, 0, 0, 0.2);
    color: #134991;
    font-size: 17px;
}

#submit {
    left: calc(25% - 50px);

}

#cancel {
    left: calc(75% - 100px);
}

button:hover {
    cursor: pointer;
}
</style>