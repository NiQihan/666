<template>
    <div class="shadow-layer">
        <div class="button-wrapper">
            <a class="close-button" @click="close"><img src="./close.svg" width="20"></a>    
        </div>
        <div class="tip-wrapper">
            <p>快速点击下面的按钮</p>
            <p>当进度条到达 100% 时抢票完成</p>
        </div>
        <div class="progress-wrapper">
            <img class="naozhong" src="./naozhong.png">
            <div class="progress-text">{{ parseInt(progress) }}%</div>
            <circle-progress
                class="circle-progress"
                :id="1"
                :width="100"
                :radius="8"
                :progress="progress"
                :barColor="'#20A0FF'"
                :backgroundColor="'#E5E9F2'"
                :isAnimation="false"
            />
        </div>
        <div class="robbing-button-wra">
            <a id="robbing-button" @click="robbing">快速点击</a>
        </div>
    </div>
</template>

<script>
import { setInterval, clearInterval } from 'timers';
import Circle_Progress from './circle-progress'
export default {
    components: {
        'circle-progress': Circle_Progress,
    },

    data: () => ({
        progress: 0,
    }),

    methods: {

        close() {
            this.$parent.show = '';
        },

        init() {
            this.progress = 0;
            this.time_handler = setInterval(() => {

                if (this.progress <= 1) 
                {
                    this.progress = 0;  
                } 
                else if (this.progress > 1 && this.progress<= 40)
                {
                    this.progress -= this.progress*0.06; 
                }
                else if (this.progress > 40 && this.progress<= 65)
                {
                    this.progress -= this.progress*0.04; 
                }
                else if(this.progress > 65 && this.progress<= 100){
                    this.progress -= this.progress*0.04; 
                }
            
                // switch(this.progress){
                // case(this.progress <= 1): alert('1'); this.progress = 0;    
                // case(this.progress > 1 && this.progress<= 50): this.progress -= this.progress*0.01; break;
                // case(this.progress > 50 && this.progress<= 85): this.progress -= this.progress*0.03; break;
                // case(this.progress > 85 && this.progress<= 100): this.progress -= this.progress*0.05; break;
                // }
            }, 100);
        },

        robbing() {
            if (this.progress >= 85) {
                clearInterval(this.time_handler);
                this.progress = 100;
                this.$parent.show = 'success-page';
            }
            else this.progress += (Math.random()*(13-8+1)+8);
        }
    }
}
</script>

<style scoped>
.circle-progress {
    position: absolute;
    top: 80px; left: 96px;
}

.shadow-layer {
    position: fixed;
    width: 100%; height: 100%;
    background-color: rgba(0, 0, 0, 0.5);
    display: flex; flex-direction: column;
    align-items: center;
}

.button-wrapper {
    position: relative;
    width: 70%;
    margin-top: 40px;
    margin-bottom: 40px;
}

.close-button {
    position: absolute;
    right: 0;
}

.close-button img {
    width: 30px;
}

.naozhong {
    width: 300px;
}

.tip-wrapper {
    text-align: center;
    font-size: 16px; color: white;
}

#progress {
    position: absolute;
    left: 0; top: 0;
}

.progress-wrapper {
    position: relative;
}

.progress-text {
    font-size: 18px;
    position: absolute;
    width: 100%; top: 115px;
    text-align: center;
}

.robbing-button-wrapper {
    display: flex;
    justify-content: center;
}

#robbing-button {
    background-color: #ED1C24;
    color: white; font-size: 16px;
    display: flex; justify-content: center; align-items: center;
    width: 160px; height: 48px;
    border-radius: 24px;
}

</style>

