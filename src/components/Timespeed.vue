<template>
    <div class="time-speed-content " :class="this.swipeUp ?'active' : ''">
        <div class="caret-swipe shadow-effects">
            <font-awesome-icon  :icon="['fas', 'angle-up']"/>
            <span  v-touch:swipe =" swipeHandler " class="span-text"> Swipe {{this.swipeUp ?'down' : 'up'}} </span >
            <font-awesome-icon  :icon="['fas', 'angle-down']" />
        </div>
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

        .caret-swipe {
            display: flex;
            flex-direction: column;
            align-content: center;
            justify-content: center;
            align-items: center;
            position: relative;
            visibility: hidden;
            @media(max-width: $mobile){
                visibility: visible;
            }
            .span-text{
                font-size: 18px;
                color:$white;
            }
            svg{
                color: $blue
            }
        }
        .shadow-effects{
            /*text-shadow: 2px 2px 5px $blue;*/
            text-shadow: 1px 1px 2px $black, 0 0 25px $blue, 0 0 5px darkblue;
            animation-name: lightening;
            animation-duration: 2s;
            animation-iteration-count: infinite;
            animation-timing-function: linear;
        }
        @keyframes lightening {
            0%{
                opacity:1
            }
            100%{
                opacity:0
            }
            
        }
        

        .time-speed-content{
            overscroll-behavior: contain;
            position: fixed;
            background: white;
            top: calc(100% - 43px);
            left:0;
            width: 100%;
            height: 100vh;
            transition: all 1s ease;
            &.active{
                top: -13px;
            }
        }

        h4{
            color: $grey-title
        }
        .speed-text{
            h3{
                color: $speed-text;
                margin:0;
            }
            p{
                font-size: 15px;
                margin:0;
            }
        }
        #result-time{
            font-size: 30px;
            font-weight: 600;
        }
        #number-6{
            @include number-speed(absolute, 127px, -8px, auto);
        }
        #number-7{
            @include number-speed(absolute, 40px, 20px, auto);
            
        }
        #number-8{
            @include number-speed(absolute, 7px, auto, 40px);
        }
            

 

</style>