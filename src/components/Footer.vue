<template>
    <div class="down text-center col-12">
        <h3>
            <a href="" target="_blank">SHARE</a>
        </h3>
        <p  v-if="result.request">
            {{result.request.responseURL}}
        </p>
    </div>
</template>
<script>

export default {
    name:'Footer',
    props: {
            result: Object
        }               
}
</script>

<style lang = "scss" scoped>
    @import "../style/app.scss";
    p{
        max-width: 400px;
        margin: 10px;
        background: $light-grey;
        border-radius: 20px;
        padding: 9px;
        cursor: pointer;
        display: inline-block;
        overflow: hidden;

        &:hover{
            text-decoration: underline;
        }
        @media(max-width:$mobile){
            max-width: 255px;
            font-size: 13px;

    }
    }
    h3{
         a{
            cursor: pointer;
            color: $black;
            text-decoration: none;
            @media(max-width:$mobile){
            font-size: 25px;
    
        }
           
            
           
        }
    }
    
 

</style>