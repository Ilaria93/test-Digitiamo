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
            margin: 10px;
            background: $light-grey;
            border-radius: 20px;
            padding: 9px;
            cursor: pointer;
            display: inline-block;

            &:hover{
                text-decoration: underline;
            }
    }
    h3{
         a{
            cursor: pointer;
            color: $black;
            text-decoration: none;
           
            
           
        }
    }
    
 

</style>