<template>
  <div class="main">
    <div>
      <el-container >
        <el-header style="text-align: right; font-size: 12px ;height:400px">
        <span>

        </span >
        </el-header>
        <div class="body">
          <el-main >
            <el-tabs  v-model="activeName" @tab-click="handleClick">
              <el-tab-pane label="队伍排名" name="first" id="teamshow">
                <div class="table_c">
                  <div class="table_all">
                    <el-card shadow="hover" class="tebale_card">
                      <el-table :data="teamData"
                                :row-class-name="tableRowClassName" :row-style="getRowClass1"
                                :header-row-style="getRowClass1" :header-cell-style="getRowClass">
                        <el-table-column type="index" :index=1 label="排名" width="200">
                        </el-table-column>
                        <el-table-column prop="name" label="团队名" width="500">
                        </el-table-column>
                        <el-table-column prop="score" label="总分" width="">
                        </el-table-column>
                      </el-table>
                    </el-card>
                  </div>
                </div>
              </el-tab-pane>
              <el-tab-pane label="个人排名" name="third">
                <div class="table_c">
                  <div class="table_all">
                    <el-card shadow="hover" class="tebale_card">
                      <el-table :data="personData"
                                :row-class-name="tableRowClassName" :row-style="getRowClass"
                                :header-row-style="getRowClass" :header-cell-style="getRowClass">
                        <el-table-column type="index"
                                         :index=1
                                         label="排名" width="120">
                        </el-table-column>
                        <el-table-column prop="numb" label="学号" width="200">
                        </el-table-column>
                        <el-table-column prop="name" label="姓名" width="200">
                        </el-table-column>
                        <el-table-column prop="class" label="班级" width="250">
                        </el-table-column>
                        <el-table-column prop="score" label="总分">
                        </el-table-column>
                      </el-table>
                    </el-card>
                  </div>
                </div>
              </el-tab-pane>
            </el-tabs>

          </el-main>
        </div>
      </el-container>
    </div>
  </div>
</template>

<script>
  export default {
    data() {
      return {
        teamData:[],
        personData:[],
        dialogTableVisible: false,
        dialogFormVisible: false,
        activeName: 'first',
      }
    },
    mounted: function () {
      setInterval(this.drawTable,1000);
      // this.drawTable();
      // console.log('开始了' + this);
      // this.initWebpack();
    },
    methods: {
      getRowClass1({row, column, rowIndex, columnIndex}) {
        return "background:#3f5c6d2c;color:#000;";
      },
      getRowClass({row, column, rowIndex, columnIndex}) {
        return "background:#3f5c6d2c;color:#000;";
      },
      tableRowClassName({row, rowIndex}) {
        row.index = rowIndex;
        if (rowIndex === 0) {
          return 'first-row';
        } else if (rowIndex === 1 || rowIndex === 2) {
          return 'second-row';
        } else
          return 'another-row';
      },
      handleClick(tab, event) {
        console.log(tab, event);
      },
      drawTable() {
        console.log('success');
        var data1 = []
        var data3 = []
        this.$axios
          .post('/index/')
          .then(response => {
            console.log('success1111');
            withCredentials: true
            for (let i = 0; i < response.data.teams.length; i++) {
              var obj = {}
            console.log(response.data);
              obj.name = response.data.teams[i].Team
              obj.score = response.data.teams[i].Score

              data1[i] = obj
            }
            for (let i = 0; i < response.data.persons.length; i++) {
              var obj = {}
              obj.numb = response.data.persons[i].Name
              obj.name = response.data.persons[i].ID
              obj.class = response.data.persons[i].Class
              obj.score = response.data.persons[i].Score
              data3[i] = obj
            }
            this.teamData = data1
            this.personData = data3
          })
          .catch(error => {
            console.log(error)
          })
      },
    }
  };

</script>

<style>
  .body .el-container .el-header {
    background-color: rgba(160, 170, 209, 0);
    color: #333;
    line-height: 60px;
  }
  .body{
    width: 85%;
    margin: auto;
    background: url(bg2.jpg) no-repeat top fixed ;
    height:100%;
    background-size:cover;
    border-radius: 15px;
    overflow: hidden;

  }
  .main{
    background: url(bg2.jpg) no-repeat top fixed ;
    height:100%;
    background-size:cover;
    border-radius: 15px;
    overflow: hidden;
  }
  .body:after{
    content: '';
    position: absolute;
    top: 0;left: 0;right: 0;bottom: 0;
    background-image: url(bg2.jpg);
    background-position: top;
    /*background: fixed;*/
    background-size: cover;
    -webkit-filter:blur(15px);
    -moz-filter:blur(15px);
    -ms-filter:blur(15px);
    -o-filter: blur(15px);
    filter: blur(15px);
    z-index: -1;
  }

  .el-table .first-row
  {
    height: 68px;
  }
  .el-table .second-row {
    height: 60px;
  }
  .el-table .first-row:hover>td {
  background: rgba(249, 218, 22, 0.53) !important;
  }
  .el-table .second-row:hover>td {
  background: rgba(190, 190, 190, 0.63) !important;
  }
  .el-table .another-row:hover>td {
  background: rgba(84, 56, 0, 0.63)!important;
  }
  #teamshow:hover>td{
  background-color: initial !important;
  }
  /*.table_c {*/
  /*width: 100%;*/
  /*background: url("bg2.jpg") center*/
  /*center no-repeat fixed;*/
  /*background-size: 100% auto;*/
  /*}*/
  .tebale_card {
    background-color: rgba(152, 112, 81, 0.46);
  }
  .el-table,
  .el-table__expanded-cell {
    background-color: #3f5c6d2c;
  }
  /deep/.el-dialog-header{
    background: #7d6149c2 !important;
  }
</style>

