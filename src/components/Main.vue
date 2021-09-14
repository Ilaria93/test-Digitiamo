<template>
     <div class="central clearfix"  v-if="result.config">
        <div class="col-12 col-md-6 float-left">
            <div class="info">
                <div id="title-column">
                    <h6>INFO</h6>
                </div>
                <div calss="info-api-elements">
                    <h6 id="title-info" >METHOD: {{result.config.method}} </h6>
                </div>
                <div calss="info-api-elements">
                    <h6 id="title-info">URL: {{result.config.url}}</h6>
                </div>
                <div calss="info-api-elements">
                    <h6 id="title-info">REQUEST:{{result.request}}</h6>
                </div>
            </div>
        </div>
        <div class="col-12 col-md-6 float-left">
            <div class="response">
                <div class="title-api-elements">
                    <h6>RESPONSE</h6>
                </div>
                <div id="api-elements">
                    <h6>HTTP: {{result.status}} {{ this.statusCodes[this.result.status]}} </h6>    
                </div>
                <div id="api-elements">
                    <h6>RESPONSE TIME: {{result.responseTimeMs}}ms</h6>
                </div>
                <div id="api-elements">
                    <h6>CONTENT-TYPE: {{result.headers['content-type'] }}</h6>
                </div>
            </div>
        </div>
    </div>
</template>

<script>

export default {
    name:'Main',
    props:{
        result: Object,
        statusCodes: Object,
    }
    
}
</script>

<style lang = "scss" scoped>
    @import "../style/app.scss";
    .central{
        width: 100%;
        margin-top: 20px;
    }
    .info, .response{
        border: 1px solid $light-grey;
        border-radius: 10px;
        padding: 15px 0;
        height: 270px;
        margin-bottom: 30px;

        @media(max-width:$mobile){
            margin-bottom: 20px;
        }
    }                   
    .info{
        background-color: $light-grey;
    }
    #title-column{
        padding: 10px;
        h6{
            @media(max-width:$mobile){
                font-size: 13px;
            }
    
        }
    }
    #title-info{
        font-weight: 600;
        background-color: $info;
        padding: 20px 10px;
        margin-bottom: 5px;
        cursor: pointer;
        overflow: hidden;
        @media(max-width:$mobile){
            font-size: 13px;
    
        }
    }
    p{
        margin-bottom: 0!important;
    }
    .title-api-elements{
        padding: 0 10px;
        h6{
            @media(max-width:$mobile){
            font-size: 13px;
    
            }
        }
    }
    
    #api-elements{
        h6{
            margin: 2px 0;
            background-color: $light-grey;
            padding: 10px 10px;
            cursor: pointer;

            &:hover{
                background-color: $info-hover;
            }
            @media(max-width:$mobile){
            font-size: 13px;
    
            }
        }
    }
    

</style>
