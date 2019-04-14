<template>
<div class="wrapper">
    <div class="message-cn">
        <p>恭喜您抢票成功</p>
        <p>我们将会尽快用短信联系您</p>
    </div>
    <div class="message-en">
        <p>Congratulations</p>
        <p>Successful ticket grabbing</p>
    </div>
    <div class="image-box">
        <img src="./success.png">
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
.message-cn {
    margin-top: 40px;
}

.message-en {
    margin-top: 30px;
}

.message-cn p {
    font-size: 16px;
    text-align: center;
    padding: 5px; margin: 0;
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

