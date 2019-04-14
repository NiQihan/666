<template>
<div class="wrapper">
    <div class="message-cn">
        <img src="./fail.png">
        <p>很遗憾您没有抢到票</p>
    </div>
    <div class="message-en">
        <p>Regrettably</p>
        <p>failed to win the ticket</p>
    </div>
    <div class="image-box">
        <img src="./lose.png">
    </div>
    <div class="button-wrapper">
        <a class="return" @click="close"> 返回首页 </a>
    </div>
</div>
</template>

<script>
export default {
    methods: {
        close() {
            this.$parent.show = '';
        }
    }
}
</script>

<style scoped>

.message-cn img {
    height: 80px;
}

.message-cn p {
    line-height: 80px;
    font-size: 20px;
    margin: 0; padding: 0;
    padding-left: 20px;
}

.message-cn {
    margin-top: 40px;
    display: flex;
    justify-content: center;
    align-content: center;
}

.message-en {
    margin-top: 30px;
}

.message-en p {
    font-size: 26px; color: #FFCAD9;
    font-weight: 800;
    text-align: center;
    padding: 5px;
    margin: 0;
}

.wrapper {
    position: absolute;
    width: 100%; height: 100%;
    left: 0; top: 0;
    background: url(./bg4.png);
    background-size: auto 100%;
}

.image-box {
    text-align: center;
}

.image-box img {
    display: inline-block;
    width: 300px;
}

.button-wrapper {
    display: flex;
    justify-content: center;
}

.return {
    display: inline-flex;
    width: 300px; height: 80px;
    background: url(./button.png);
    background-size: 100% ;
    font-size: 20px; color: white;
    justify-content: center; align-items: center;
}
</style>

