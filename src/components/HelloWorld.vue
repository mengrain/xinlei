<template>
  <div class="hello">
   <el-button type="text" @click="dialogFormVisible = true">添加</el-button>

<el-dialog title="难受" :visible.sync="dialogFormVisible">
  <el-form :model="form">
  	
    <el-form-item label="名字" :label-width="formLabelWidth">
      <el-input v-model="form.name" ></el-input>
    </el-form-item>
    
    <el-form-item label="性别" :label-width="formLabelWidth">
      <el-input v-model="form.sex" ></el-input>
    </el-form-item>
    
    <el-form-item label="state" :label-width="formLabelWidth">
      <el-input v-model="form.state"></el-input>
    </el-form-item>
  </el-form>
  
  <div slot="footer" class="dialog-footer">
    <el-button type="primary"  @click="btn">确 定</el-button>
  </div>
  
</el-dialog>
  </div>
</template>

<script>
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
   data() {
      return {
        arr: [],
        dialogTableVisible: false,
        dialogFormVisible: false,
        form: {
        	name:'',
        	sex:'',
        	state:'',
        },
        formLabelWidth: '120px'
      };
   },
   methods:{
			btn(row){
				this.$http.post('http://localhost:3000/add',{name:this.form.name,sex:this.form.sex,state:this.form.state},{ emulateJSON: true }).then(function(){
					this.arr.push(this.form)
				})
			},
		}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
input{
	float: left;
	width: 150px;
	height: 30px;
}
</style>
