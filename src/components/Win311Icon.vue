<template>
    <div class="icon" @click="bg_blue()" @dblclick="alert()">
        <img :src="require(`@/assets/icons/${this.name + '.png'}`)" />
        <div class="app-name" :style="{background: color}">{{ this.name }}</div>
    </div>
</template>

<script>
export default {
    props: {
        name: String
    },
    data () {
        return {
            color: "hidden",
            aux: 0
        };
    },
    methods: {
        bg_blue: function(event) {
            if (this.aux === 0) {
                this.aux++;
                this.color = "blue";
            } else {
                this.color = "none";
                this.aux = 0;
            }
        },
        alert: function(event) {
            alert("Open " + this.name);
        }
    }
};
</script>

<style>

</style>