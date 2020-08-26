<template>
  <div class="window">           
    <div class="header">
        <div class="line">&#8212</div>
        <div class="title">{{ title }}</div>
        <div class="arrow">&#9660</div>
    </div>
    <div class="container">
        <div class="nav-bar">
            <div class="nav-bar-item1">Settings</div>
            <div class="nav-bar-item2">Help</div>
        </div>
        <div class="body">
            <div class="icons">
                <win311-icon v-for="(name, i) in this.icons" :name="icons[i]" :key="i"></win311-icon>
            </div>
        </div>
    </div>
    <div class="footer">Select app to open...</div>
  </div>
</template>

<script>
import json from '../assets/windows.json';
import Win311Icon from './Win311Icon';

export default {
    components: {
        "win311-icon": Win311Icon
    },
    props: {
        type: {
            type: String
        }
    },
    data() {
        return {
            title: json[this.type].title,
            icons: json[this.type].icons
        };
    }
}
</script>

<style>
    .window {
        background: lightgrey;
        width: 650px;
        height: 300px;
        margin: auto;
    }
    .header {
        display: flex;
        width: 100%;
        height: 35px;
        align-items: center;
    }
    .line { 
        margin-left: 15px;
    }
    .title {
        color: white;
        font-size: 20px;
        background: darkblue;
        width: 90%;
        margin-left: 15px; 
        margin-right: 15px;       
    }
    .arrow {
        margin-right: 15px;
    }
    .container {
        background: white;
        height: 230px;
        width: 630px;
        margin-top: 50px;
        margin: auto;
    }
    .nav-bar {
        display: flex;
        height: 30px;
        width: 100%;
        border-bottom: 1px solid black;
        align-items: center;
    }
    .nav-bar-item1 {
        height: auto;
        width: 15%;
    }
    .nav-bar-item1:hover {
        background-color: black;
        color:white;
    }
    .nav-bar-item2 {
        height: auto;
        width: 15%;
    }
    .nav-bar-item2:hover {
        background: black;
        color:white;
    }
    .body {
        margin-top: 15px;
        display: flex;  
    }
    .icons {
        display: grid;
        grid-template-columns: repeat(7, 1fr);
        grid-gap: 15px 15px;
    }
    .footer {
        display: flex;
        height: 35px;
        width: 100%;
        align-items: center;
        margin-left: 15px;
    }
</style>