<template>
  <div class="hello">

     <div>
      <input type='checkbox' class='input-checkbox' v-model='allChecked' @click='checkedAll'>全选
      <template v-for='checkb in checkboxData'>
         <input type='checkbox' name='checkboxinput' class='input-checkbox' v-model='checkboxModel' :value='checkb'>{{checkb.value}}
      </template>
      <input type='checkbox' class='input-checkbox' v-model='uu'>选择1
      <input type='checkbox' class='input-checkbox' v-model='tt'>选择2
      <div>你的选择:{{checkboxModel}}</div>
    </div>
   
  </div>
</template>

<script>
export default {
  name: 'hello',
  data () {
    return {
      checkboxData:[{
        id:'1',
        value:'苹果'
      },{
        id:'2',
        value:'荔枝'
      },{
        id:'3',
        value:'香蕉'
      },{
        id:'4',
        value:'火龙果'
      }],
      checkboxModel:[],
      allChecked:"",
      uu:"",
      tt:"123"
    }
  },
  methods:{

    checkedAll: function() {
      var _this = this;
      if(!this.allChecked){
        this.checkboxModel =[];
      }
      if(this.allChecked){
        this.checkboxModel =[];
        var that = this
        this.checkboxData.map((item,index)=>{
          that.checkboxModel.push(item);
        })
        
      }
     
    }
  },
  watch:{
     'checkboxModel': {
      handler: function (val, oldVal) { 
        if (this.checkboxModel.length === this.checkboxData.length) {
          this.allChecked=true;
        }else{
          this.allChecked=false;
        }
      },
      deep: true
    }

  },
   beforeRouteEnter: function (to,from,next) {
        next(vm => {
          vm.uu =''
          debugger
          vm.tt=''
        })
      }


}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
