<template>
    <div class="time-speed-content " :class="this.swipeUp ?'active' : ''">
        <div class="caret-up"></div>
        <span  v-touch:swipe =" swipeHandler " > Swipe up </span >
        <div class="time-analysis col-12">
            <h4>Time Analysis</h4>
            <div class="speed-up">
                <div class="speedometer">
                    <div id="main-div">
                        <div class="layout-align">
                            <div class="number-speedometer">
                                <p id="number-6">600</p>
                                <p id="number-7">700</p>
                                <p id="number-8">800</p>
                            </div>
                            <div id="score-meter-1" class="layout-align">
                                <div id="scorer-1-inner-div">
                                    <div id="scorer-1-inner-div-5">
                                        <div class="scorer-1-tick">
                                            <div class= "ball-tick"></div>
                                        </div>
                                    </div>
                                    <p id="result-time">{{result.responseTimeMs}}ms</p>       
                                </div>
                                <div id="scorer-1-inner-div-2"></div>
                                <div id="scorer-1-inner-div-3"></div>
                                <div id="scorer-1-inner-div-4"></div>
                                <div id="scorer-1-inner-div-6"></div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="speed-text text-center">
                    <h3>Page Load</h3>
                    <p>{{ (result.responseTimeMs / 1000).toFixed(2)}}s</p>
                </div>
            </div>
            <div class="speed-down">
                <div class="speedometer">
                    <div id="main-div">
                        <div class="layout-align">
                            <div class="number-speedometer">
                                <p id="number-6">600</p>
                                <p id="number-7">700</p>
                                <p id="number-8">800</p>
                            </div>
                            <div id="score-meter-1" class="layout-align">
                                <div id="scorer-1-inner-div">
                                    <div id="scorer-1-inner-div-5">
                                        <div class="scorer-1-tick">
                                            <div class= "ball-tick"></div>
                                        </div>
                                    </div>
                                        <p id="result-time">{{result.responseTimeMs}}ms</p>                 
                                </div>
                                <div id="scorer-1-inner-div-2"></div>
                                <div id="scorer-1-inner-div-3"></div>
                                <div id="scorer-1-inner-div-4"></div>
                                <div id="scorer-1-inner-div-6"></div>
                            </div>
                        </div>
                    </div>
                </div>
                <div class="speed-text text-center">
                    <h3>First Interaction</h3>
                    <p>{{ (result.responseTimeMs / 1000).toFixed(2)}}s</p>
                </div>
            </div>
        </div>
    </div>
</template>
<script>

//import Vue2TouchEvents from 'vue2-touch-events'


export default {
    
    name:'Timespeed',
    components:{
    },
    props:{
        result: Object
    },
    methods: {
        swipeHandler: function(direction){
            if (direction =='top') {
                this.swipeUp = true 
                
            }else if (direction== 'bottom') {
                this.swipeUp = false
                
            }
 
            

            console.log(direction);


        }
        

    },
    data(){
        return{
            swipeUp: false
        }
    },
        
}
</script>

<style lang = "scss" scoped>
    @import "../style/app.scss";

        .caret-up {
            position: relative;
            display: inline-block;
            top: -35px;
            }

            .caret-up:before {
            content: '';
            position: absolute;
            top: 0;
            left: 0;
            border-bottom: 20px solid #0045ff;
            border-left: 20px solid transparent;
            border-right: 20px solid transparent;
            }

            .caret-up:after {
            content: '';
            position: absolute;
            left: 4px;
            top: 4px;
            border-bottom: 16px solid #fff;
            border-left: 16px solid transparent;
            border-right: 16px solid transparent;
            }

        .time-speed-content{
            position: fixed;
            background: white;
            top: calc(100% - 30px);
            left:0;
            width: 100%;
            min-height: 100vh;
            transition: all 1s ease;
            &.active{
                top:0;
            }

            @media(max-width: $mobile){
                display: block;
            }
        }

        h4{
            color: $grey-title
        }
        .speed-text{
            h3{
                color: $speed-text;
            }
            p{
                font-size: 15px;
            }
        }
        #result-time{
            font-size: 30px;
            font-weight: 600;
        }
        #number-6{
            @include number-speed(absolute, 134px, 0, auto);
        }
        #number-7{
            @include number-speed(absolute, 45px, 30px, auto);
            
        }
        #number-8{
            @include number-speed(absolute, 7px, auto, 40px);
        }
            

 

</style>