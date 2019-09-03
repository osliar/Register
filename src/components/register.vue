<template>
  <div class="regis">
    <div class="head">
      <span class="title">网络安全大赛注册</span>
      <div class="menu_all">
        <ul class="menu">
          <li><router-link to='/register'>注册</router-link></li>
          <li><router-link to='/success'>查询</router-link></li>
      </ul>
      </div>

    </div>
    <div class="table">
    <el-form :model="ruleForm"  :rules="rules" ref="ruleForm" :inline="true" label-width="100px">
      <el-row  :gutter="20" style="margin-top: 50px">
        <el-col :span="4"><div class="test"><p class="tip"></p></div></el-col>
        <el-col :span="5"><el-form-item  prop="team"><el-input v-model="ruleForm.team" clearable><template slot="prepend">队名</template></el-input></el-form-item></el-col>
      </el-row>
      <el-row  :gutter="20">
        <el-col :span="4"><div class="test"><p class="tip">队长</p></div></el-col>
        <el-col :span="4"><el-form-item  prop="name1"><el-input placeholder="" v-model="ruleForm.name1" clearable><template slot="prepend">姓名</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="stuid1"><el-input placeholder="" v-model.number="ruleForm.stuid1" clearable><template slot="prepend">学号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="classname1"><el-input placeholder="例如：计科1801" v-model="ruleForm.classname1" clearable><template slot="prepend">专业班级</template></el-input></el-form-item></el-col>
      </el-row>
      <el-row  :gutter="20">
        <el-col :span="4">&nbsp;</el-col>
        <el-col :span="4"><el-form-item  prop="email1"><el-input placeholder="" v-model="ruleForm.email1" clearable><template slot="prepend">邮箱</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="phone1"><el-input placeholder="" v-model.number="ruleForm.phone1" clearable><template slot="prepend">手机号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="qq1"><el-input placeholder="" v-model.number="ruleForm.qq1" clearable><template slot="prepend">QQ</template></el-input></el-form-item></el-col>
      </el-row>
      <br>
      <el-row  :gutter="20">
        <el-col :span="4"><div class="test"><p class="tip">队员1</p></div></el-col>
        <el-col :span="4"><el-form-item  prop="name2"><el-input placeholder="" v-model="ruleForm.name2" clearable><template slot="prepend">姓名</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="stuid2"><el-input placeholder="" v-model.number="ruleForm.stuid2" clearable><template slot="prepend">学号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="classname2"><el-input placeholder="" v-model="ruleForm.classname2" clearable><template slot="prepend">专业班级</template></el-input></el-form-item></el-col>
      </el-row>
      <el-row  :gutter="20">
        <el-col :span="4">&nbsp;</el-col>
        <el-col :span="4"><el-form-item  prop="email2"><el-input placeholder="" v-model="ruleForm.email2" clearable><template slot="prepend">邮箱</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="phone2"><el-input placeholder="" v-model.number="ruleForm.phone2" clearable><template slot="prepend">手机号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="qq2"><el-input placeholder="" v-model.number="ruleForm.qq2" clearable><template slot="prepend">QQ</template></el-input></el-form-item></el-col>
      </el-row>
      <br>
      <el-row  :gutter="20">
        <el-col :span="4"><div class="test"><p class="tip">队员2</p></div></el-col>
        <el-col :span="4"><el-form-item  prop="name3"><el-input placeholder="" v-model="ruleForm.name3" clearable><template slot="prepend">姓名</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="stuid3"><el-input placeholder="" v-model.number="ruleForm.stuid3" clearable><template slot="prepend">学号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="classname3"><el-input placeholder="" v-model="ruleForm.classname3" clearable><template slot="prepend">专业班级</template></el-input></el-form-item></el-col>
      </el-row>
      <el-row  :gutter="20">
        <el-col :span="4">&nbsp;</el-col>
        <el-col :span="4"><el-form-item  prop="email3"><el-input placeholder="" v-model="ruleForm.email3" clearable><template slot="prepend">邮箱</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="phone3"><el-input placeholder="" v-model.number="ruleForm.phone3" clearable><template slot="prepend">手机号</template></el-input></el-form-item></el-col>
        <el-col :span="6"><el-form-item  prop="qq3"><el-input placeholder="" v-model.number="ruleForm.qq3" clearable><template slot="prepend">QQ</template></el-input></el-form-item></el-col>
      </el-row>
      <el-row :gutter="20">
        <el-col :span="12" :offset="6">
          <el-form-item>
          <el-button type="primary"  v-model="ruleForm.register" @click="submitForm('ruleForm')" class="register-btn">提交</el-button>
        </el-form-item>
        </el-col>
      </el-row>
    </el-form>
    </div>
    <div class="footer">
      <a :href ="'http://hxb.hunan.gov.cn/message'">CTF平台</a> | <a :href = "'https://school.futurelab.tv/'">睡前带你看未来平台</a>
      <p>校赛交流群：528047282</p>
      <p>© 网络安全实验室</p>
    </div>
  </div>
</template>

<script>
    export default {
      data() {
        var checkPhone = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('请输入手机号'));
          } else {
            const reg = /^1[3|4|5|7|8][0-9]\d{8}$/
            console.log(reg.test(value));
            if (reg.test(value)) {
              callback();
            } else {
              return callback(new Error('请输入正确的手机号'));
            }
          }
        };
        var checkStu = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('请输入学号'));
          } else {
            const reg = /^1[6|5|7|8][1][1|2]\d{7}$/
            console.log(reg.test(value));
            if (reg.test(value)) {
              callback();
            } else {
              return callback(new Error('请输入正确的学号'));
            }
          }
        };
        var checkQQ = (rule, value, callback) => {
          if (!value) {
            return callback(new Error('请输入QQ'));
          } else {
            const reg = /^[1-9][0-9]\d{4,8}$/
            console.log(reg.test(value));
            if (reg.test(value)) {
              callback();
            } else {
              return callback(new Error('请输入正确的QQ'));
            }
          }
        };
        return {
          rules: {
            team:[{ required: true, message: '请输入队名', trigger: 'blur' }, { min: 2, max: 10, message: '队名长度在 2 到 10 个字符', trigger: 'blur' }],
            email1:[{ required: true, message: '请输入邮箱地址', trigger: 'blur' }, { type:'email', message: '请输入正确的邮箱地址', trigger: 'blur' }],
            email2:[{ required: true, message: '请输入邮箱地址', trigger: 'blur' }, { type:'email', message: '请输入正确的邮箱地址', trigger: 'blur' }],
            email3:[{ required: true, message: '请输入邮箱地址', trigger: 'blur' }, { type:'email', message: '请输入正确的邮箱地址', trigger: 'blur' }],
            name1:[{ required: true, message: '请输入姓名', trigger: 'blur' }],
            name2:[{ required: true, message: '请输入姓名', trigger: 'blur' }],
            name3:[{ required: true, message: '请输入姓名', trigger: 'blur' }],
            classname1:[{ required: true, message: '请输入专业班级', trigger: 'blur' }],
            classname2:[{ required: true, message: '请输入专业班级', trigger: 'blur' }],
            classname3:[{ required: true, message: '请输入专业班级', trigger: 'blur' }],
            qq1:[{ validator:checkQQ, trigger: 'blur' }],
            qq2:[{ validator:checkQQ, trigger: 'blur' }],
            qq3:[{ validator:checkQQ, trigger: 'blur' }],
            stuid3:[{ validator:checkStu, trigger: 'blur' }],
            stuid2:[{ validator:checkStu, trigger: 'blur' }],
            stuid1:[{ validator:checkStu, trigger: 'blur' }],
            phone3:[{ validator:checkPhone, trigger: 'blur' }],
            phone2:[{ validator:checkPhone, trigger: 'blur' }],
            phone1:[{ validator:checkPhone, trigger: 'blur' }],
          },
          background: {
            backgroundImage: "url(" + require("../assets/bg1.jpg") + ")",
            backgroundPosition: "center center",
            backgroundRepeat: "no-repeat",
            backgroundSize: "cover",
          },
          ruleForm: {
            team: '',
            name1: '', name2: '', name3: '',
            qq1: '', qq2: '', qq3: '',
            email1: '', email2: '', email3: '',
            phone1: '', phone2: '', phone3: '',
            stuid1: '', stuid2: '', stuid3: '',
            classname1: '', classname2: '', classname3: '',
          },
        }
      },
      methods: {
        submitForm(formName) {
          this.$refs[formName].validate((valid) => {
            if (valid) {
          this.$confirm('请检查无误后进行提交！', '确认信息', {
            distinguishCancelAndClose: true,
            confirmButtonText: '确认提交',
            cancelButtonText: '取消'
          })
            .then(() => {
              this.$axios
                .post('/api/register/', this.$qs.stringify(this.ruleForm), {headers: {'Content-Type': "application/x-www-form-urlencoded"}})
                .then(response => {
                  console.log(this.$qs.stringify(this.ruleForm))
                  withCredentials: true
                  if (response.data.code == 204) {
                    this.$message.error("存在用户已经注册或正在审核");
                    return false;
                  }
                  else if (response.data.code == 202) {
                    this.$message.error("该队名已经注册！");
                    return false;
                  }
                  else {
                    this.$confirm('请等待审核！', '成功提交', {
                      confirmButtonText: '确定',
                      showCancelButton: false,
                      type: 'success',
                      center: true
                    }).then(() => {
                      this.$router.push('/success')
                    }).catch(() => {

                    });
                    return true;
                  }
                })
                .catch(error => {
                  console.log(error)
                })
            })
            .catch(action => {
              this.$message.info("取消提交")
            });
        } else {
          return false;
           }
        })
        },
      }
    }
</script>

<style scoped>
    .head{
      width: 100%;
      height: 90px;
      background-color: lightblue;
      padding: 0;
      margin: 0;
    }
  .title{
    font-family: 幼圆;
    font-size: 2em;
    color: white;
    float: left;
    margin-top: 30px;
    margin-left: 50px;
  }
  .tip{
    text-align: right;
  }
  .table {
    margin: auto;
  }
  .register-btn{
      width: 100%;
  }
  .footer{
    width: 100%;
    height: auto;
    background-color: aliceblue;
    padding-top: 20px;
    color: dimgray;
  }
  .footer a{
    text-decoration: none;
    color: darkgray;
    font-size: 1.1em;
  }
  a{
    text-decoration: none;
  }
  ul{
    float: right;
    list-style-type:none;
    margin-right: 50px;
    height:40px;
  }
  ul li{
    width: 100px;
    float: left;
    text-align: center;
    color: white;
    line-height: 40px;
  }
  .menu_all{
    padding-top: 30px;
    color: white;
    font-size: 1.1em;
  }
</style>
