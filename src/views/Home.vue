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
      </tr>
      </thead>
        <tbody>
        <td> {{disasters.messageType}}</td>
        <td> {{disasters.disasterCategory}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[0].expectedAshFall}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[0].localGovernment}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[0].warningCode}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[1].expectedAshFall}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[1].localGovernment}}</td>
        <td> {{disasters.ashFallTimeWarningCodeLocalGovernments[1].warningCode}}</td>
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
        }
    }
  }
}
</script>
  
