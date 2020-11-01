<template>
  <div id="app">

    <table class="table">
      <thead class="thead-lignt">
      <tr>
        <th>MessageType</th>
        <th>DisasterCategory</th>
        <th>ExpectedAshFall_1</th>
        <th>LocalGovernment_1</th>
        <th>WarningCode_1</th>
        <th>ExpectedAshFall_2</th>
        <th>LocalGovernment_2</th>
        <th>WarningCode_2</th>
        <th>ExpectedAshFall_3</th>
        <th>LocalGovernment_3</th>
        <th>WarningCode_3</th>
        <th>ExpectedAshFall_4</th>
        <th>LocalGovernment_4</th>
        <th>WarningCode_4</th>
      </tr>
      </thead>
        <tbody>
       <tr v-for="disaster in disasters" v-bind:key="disaster">
        <td> {{disaster.messageType}}</td>
        <td> {{disaster.disasterCategory}}</td>   
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[0].expectedAshFall}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[0].localGovernment}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[0].warningCode}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[1].expectedAshFall}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[1].localGovernment}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[1].warningCode}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[2].expectedAshFall}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[2].localGovernment}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[2].warningCode}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[3].expectedAshFall}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[3].localGovernment}}</td>
        <td> {{disaster.ashFallTimeWarningCodeLocalGovernments[3].warningCode}}</td>
        <v-for/>
        </tr>
        </tbody>
      </table>
  </div>
</template>
<script>
export default {
  name: 'home',
  data:function() {
    return{
        disasters:null
    }
  },
   mounted :function(){
     this.todo()
   },
   methods:{
     todo : function(){
        var sse = new EventSource("/sse");
        var self=this;
        sse.onmessage = function (evt) {
        self.disasters=JSON.parse(evt.data);  
        console.log(self.disasters)
       }
    }
  }
}
</script>

    <!--v-for disaster in disasters-->
    <!--/v-for-->
  
