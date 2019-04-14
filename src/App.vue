<template>
<main>
    <div class="layer main-page">

        <div class="menu-wrapper">
            <div class="menu">
                <div class="slider" :class="{right: user === 'others'}"></div>
                <a :class="{ student: true, selected: user === 'student'}" @click="user = 'student'"> 学生 </a>
                <a :class="{ others: true, selected: user === 'others'}" @click="user = 'others'"> 其他 </a>
            </div>
        </div>

        <div class="tip">
            &lt;填写的信息将作为取票时的凭证&gt;
        </div>

        <div class="form-wrapper">
            <form>

                <label>
                    <img src="./name.jpg">
                    <input type="text" v-model="input_name" placeholder="您的真实姓名">
                </label>

                <label>
                    <img src="./id.jpg">
                    <input type="text" v-model="input_id" :placeholder="user === 'student'? '您的西电学号' : '您的身份证号码'">
                </label>

                <label>
                    <img src="./phone.jpg">
                    <input type="text" v-model="input_phone" placeholder="您的联系电话">
                </label>

                <a class="start-robbing" @click="check_input_and_robbing"> 参与抢票 </a>
            </form>
        </div>       

        <div class="counting-wrapper">
            <img src="./gif.gif">
            <div class="">
                <div class="message"> 距离校歌赛抢票开始还剩： </div>
                <div class="resting-time">{{ hour }}: {{ minute }}: {{ second }}</div>
            </div>
        </div>
    </div>
    <robbing-page ref="robbing_page" v-show="show === 'robbing-page'"/>
    <success-page ref="success_page" v-show="show === 'success-page'"/>
    <failure-page ref="failure_page" v-show="show === 'failure-page'"/>
</main>
</template>

<script>
import Robbing_Page from './robbing-page.vue'
import Success_Page from './success-page.vue'
import Failure_Page from './failure-page.vue'

export default {
    components: {
        'robbing-page': Robbing_Page,
        'success-page': Success_Page,
        'failure-page': Failure_Page,
    },

    data: () => ({
        show: '',
        user: 'student',
        input_name: '',
        input_id: '',
        input_phone: '',
        hour: '00',
        minute: '00',
        second: '00',
    }),

    methods: {

        start_robbing() {
            this.$refs.robbing_page.init();
            this.show = 'robbing-page';
        },

        check_input_and_robbing() {

            if (this.input_name.trim() === '') {
                alert('姓名不能为空');
                return;
            }

            if (this.user === 'student') {
                if (!/\d{11}/.test(this.input_id.trim())) {
                    alert('学号需要是 11 位数字');
                    return;
                }
            }
            else {
                if (!/\d{18}/.test(this.input_id.trim())) {
                    alert('身份证号需要是 18 位数字');
                    return;
                }
            }            

            if (!/\d{11}/.test(this.input_phone.trim())) {
                alert('电话需要是 11 位数字');
                return;
            }

            this.$refs.robbing_page.init();
            this.show = 'robbing-page';
        },
    }
}
</script>

<style scoped>

.main-page {
    background: url(./background.png);
    background-size: 100%;
}

.selected {
    color: black;
}

.message {
    font-size: 16px; color: white;
}

.resting-time {
    font-size: 36px; color: white;
    margin-top: 10px;
}

.counting-wrapper {
    margin-top: 80px;
    display: flex;
    justify-content: center;
}

.counting-wrapper img {
    height: 80px;
}

.start-robbing {
    display: block;
    width: 80%;
    height: 50px; line-height: 50px;
    position: absolute;
    bottom: -25px;
    box-shadow: 0 3px 5px #dd4176;
    font-size: 16px;
    /* border: 1px solid black; */
    left: 10%;
    background: linear-gradient(to right, #F84C88 , #FBA169);
    border-radius: 5px;
    color: white;

}

label img {
    display: block;
    height: 30px;
    position: absolute;
    top: 5px;
}

label input {
    all: unset;
    display: block;
    height: 40px;
    border-bottom: 1px #F1F1F1 solid;
    font-size: 16px;
    text-align: left;
    padding-left: 40px;
    /* border: 1px solid black; */
    flex-grow: 1;
}

label {
    position: relative;
    display: flex;
    justify-content: stretch;
    align-items: stretch;
    margin-top: 10px;
    padding: 0 20px;
}

.form-wrapper {
    display: block;
    text-align: center;
    width: 100%;
}

form {
    display: inline-block;
    position: relative;
    background-color: white;
    border-radius: 10px;
    width: 75%;
    padding-top: 5px;
    padding-bottom: 40px;
}

.menu-wrapper {
    width: 100%;
    margin-top: 100px;
    text-align: center;
}

.menu {
    display: inline-block;
    width: 200px; height: 40px;
    background-color: rgba(0, 0, 0, 0.3);
    border-radius: 20px;
    position: relative;
    color: white;
}

.slider {
    position: absolute; top: 3px; left: 3px;
    height: 34px; width: 100px;
    border-radius: 17px;
    background-color: white;
    transition: left 0.5s;
}

.right {
    left: 97px;
    transition: left 0.5s;
}

.menu a {
    position: absolute;
    width: 100px; height: 40px;
    display: block;
    font-size: 16px;
    line-height: 40px;
    text-align: center;
}

.student {
    left: 0; top: 0;
    
}

.others {
    right: 0; top: 0;
}

.layer {
    position: fixed;
    width: 100%; height: 100%;
    left: 0; top: 0;
    background-color: grey;
}

/* .home {
    overflow: hidden;
} */

/* #background {
    width: 375px;
} */

/* #student {
    all: unset;
    font-size: 16px;
    position: absolute;
    left: 121px; top: 185px;
}

#others {
    all: unset;
    color: white;
    font-size: 16px;
    position: absolute;
    left: 228px; top: 185px;
} */

.tip {
    margin: 10px 0;
    font-size: 14px; color: white;
    text-align: center;
}

 /* #start-robbing-button {
    height: 40px; width: 220px;
    left: 80px; top: 390px;
    display: flex; justify-content: center; align-items: center;
    font-size: 16px; color: white;
    position: absolute;

}  */
</style>
