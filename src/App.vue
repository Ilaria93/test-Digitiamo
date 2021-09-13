<template>
  <div id="app">
    <div class="container">
        <div class="row pb-5">
          <div class="col-12">
            <header class="text-center row">
                <div class="title-page col-12 col order-2 col-md-12 order-md-1">
                    <h1>{{result.status }}</h1>
                    <p>{{ this.statusCodes[this.result.status]}}</p>
                </div>
                <div class ="col-12 order-1 offset-md-3 col-md-6 order-md-2"> 
                    <div class="central-input "> 
                        <select v-model="method" id="method">
                            <option v-for= "(method, index) in methods_data" :key = "index">{{method}}</option>
                        </select>
                        <input v-model= "apiAddress" id="site-input" type="text">
                        <button @click="sendRequest" type="button" class="btn btn-primary" id = "send-btn">SEND</button>
                    </div>
                </div>
            </header>    
          </div>

    <Main :result="this.result" :statusCodes="this.statusCodes" />
    <Footer :result="this.result"/>
    <Timespeed :result="this.result"/>
    
      </div>
    </div>
  </div>
</template>

<script>
import Main from './components/Main.vue';
import Footer from './components/Footer.vue';
import Timespeed from './components/Timespeed.vue';
import axios from 'axios'


export default {
  name: 'App',
  components: {
    Main,
    Footer,
    Timespeed
  },
  created(){},
  data(){
        return {
          result:{},
          apiAddress: 'http://localhost:3000/todo',
          method:'GET',
          methods_data:[
              'GET',
              'POST',
              'PUT',
              'PATCH',
              'DELETE'
          ],
          statusCodes: {
              200: 'Everithing is fine! :)',
              201:' Created',
              203: 'Non-Authoritative Information',
              204: 'No-content',
              301: 'Moved Permanently',
              400: 'Bad Request',
              401: 'Unauthorized',
              403: 'Forbidden',
              404: 'Not Found',
              405: 'Method Not Allowed',
              500: 'Internal Server Error',
              501: 'Not implemented',
          }
        }
  },
    methods:{
        sendRequest: function(){
          this.result = {};
          const self = this;
          const sendDate = (new Date()).getTime();
            axios({method: self.method, url: self.apiAddress,}).then((result) =>{
                console.log(result);
                self.result= result;
            const receiveDate = (new Date()).getTime();
            const responseTimeMs = receiveDate - sendDate;
            self.result.responseTimeMs = responseTimeMs;
            console.log(responseTimeMs);
            }).catch(error => {
              self.result.status= error.response.status 
              self.$forceUpdate()
              
            });
        },
        

    }
  }
</script>

<style lang="scss">
  @import "./style/app.scss";

  .central-input{
        background-color: $light-grey;
        border-radius: 5px;
        padding: 8px;
        @include flex(row, nowrap, space-between,center);
        align-content: center;
        margin: 15px auto;
        }

    #method{
        height: 36px;
        background-color: $white;
        border: 0;
        border-radius: 10px;
        padding-left: 5px;
        }
    
    #site-input { 
        padding: 5px;                             
        border: 0;
        width: 70%;
        background: none;
        }
    
    #send-btn{
        padding: 5px 20px;
        border-radius: 6px;
        }
    
</style>
