<template>
  <div class="home">
     <el-table
      :data="arr"
      style="width: 100%">
      <el-table-column
        prop="id"
        label="学号"
         width="180">
      </el-table-column>
      <el-table-column
        prop="name"
        label="姓名"
        width="180">
      </el-table-column>
      <el-table-column
        prop="sex"
        label="性别"
        width="180">
      </el-table-column>
       <el-table-column label="操作">
      <template slot-scope="scope">
       
        <el-button
          size="mini"
          type="danger"
          @click="handleDelete(scope.row)">删除</el-button>
      </template>
    </el-table-column>
    </el-table>
    
    <HelloWorld />
    
  </div>
</template>

<script>
// @ is an alias to /src
import HelloWorld from '@/components/HelloWorld.vue'

export default {
  name: 'home',
  components: {
    HelloWorld
  },
   data() {
        return {
          arr:[],
          zys:{}
        }
      },
      watch:{
      	'$route':function(){
      		 this.fz();
      	}
      },
      created() {
			 this.fz()
		},
		methods:{
			fz(){
				this.$http.post('http://localhost:3000',{state:this.$route.params.id},{ emulateJSON: true }).then(e => this.arr = e.body)
			},
			handleDelete(row){
				this.$http.post('http://localhost:3000/del',{id:row.id},{ emulateJSON: true }).then(e => row.id = e.body)
				 var _index = this.arr.indexOf(row)
         this.arr.splice(_index,1)			
			},
		}
		
}
</script>
