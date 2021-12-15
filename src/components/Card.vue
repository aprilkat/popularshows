<template>
    <div class="Card" v-bind:img='poster_path' v-bind:imglink='imglink'>
        <img :src="imglink + img" >
        <h2  >{{title}}</h2>
        <p  b-bind:overview='overview'>{{overview}}</p>
    </div>
</template>

<script>
export default {
    name: "Card",
    props: ['title', 'overview', 'imglink', 'img']
    }
</script>

<style scoped>
    .Card{
        display: inline-block;
        width: 30%;
        padding: 5px;
        margin: 10px;
        box-shadow: 10px 10px 5px grey;

    }

    img{
        width: 95%
    }

    h2{
        font-size: 30px;
    }

    p {
        font-size: 20px;    }
</style>