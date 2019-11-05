<template>
  <div class="kc-center">
   <el-form ref="rf"
   	    :lable-position="pst"
            :model="obj" 
	    :rules="rul"
            class="kc-form" 
	    label-width="60px"
	    >
     <el-form-item label="用户名:">
     <el-input v-model="obj.user" 
               placeholder="请输入用户名"
	       maxlength="20"
               show-word-limit
               clearable
               ></el-input>
     </el-form-item>
     <el-form-item label="密码:">
     <el-input v-model="obj.passwd" 
      	       placeholder="请输入密码"
	       show-password
               clearable
	       ></el-input>
     </el-form-item>
     <el-button :type="bty"
        	:loading="bst"
		@click="login('rf')"
		round
		>{{bms}}</el-button>
   </el-form>
  </div>
</template>

<style>
.kc-center {
   padding: 5px;
}
.kc-form {
   padding: 3px;
   box-shadow: 0 2px 4px rgba(0, 0, 0, .12), 0 0 6px rgba(0, 0, 0, .04);
}
</style>

<script>
export default {
 data() {
   return {
      pst: "left",
      obj:{
        user: "king",
        passwd: "123456"
      },
      rul:{
	user: [
	      {validator: function(r,v,c){
                  c(new Error(v+" error!"))
				    }, trigger:"blur"}
	],
	passwd: [
              {validator: function(r,v,c){
                  c(new Error(v+" error!"))
				   }, trigger:"blur"}
	]
      },
      bty:"",
      bst: false,
      bms: "开始登录"
   } 
 },
 methods: {
     login(rf) {
	this.$refs[rf].validate((valid) => {
	   if(valid) {
	        this.bty="primary"
	        this.bst=true
	        this.bms="登录中..."
	     }else{
	        return false
	     }
        })
    }
 }
}
</script>
