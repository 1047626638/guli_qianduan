 <template>
    <div class="app-container">
        讲师列表
    </div>
</template>

<script>
    //引入teacher.js文件
   import teacher from '@/api/edu/teacher'

   export default{
       //写核心代码位置
       data(){ //定义变量和初始值
           return{
               list:null,//查询之后接口返回集合
               page:1,//当前页
               limit:10,//每页记录数
               total:0,//总记录数
               teacherQuery:{} //条件封装对象
           }
       },
       created(){ //页面渲染之前执行，一般调用methods定义的方法
            this.getList()
       },
       methods:{ //创建具体的方法，调用teacher.js定义的方法
            getList(){
                teacher.getTeacherListPage(this.page,this.limit,this.teacherQuery)
                .then(response =>{//请求成功
                     //response 接口返回的数据
                    // console.log(response)
                   this.list = response.data.list
                   this.total = response.data.total
                   console.log(this.list)
                   console.log(this.total)
                }).catch(error =>{
                    console.log(error);
                    
                })
            }

       }
   }
</script>
