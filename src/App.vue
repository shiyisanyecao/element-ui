<template>
  <div id="app">
    <!-- <el-button-group>
      <el-button type="primary" icon="el-icon-arrow-left">
        上一页
      </el-button>
      <el-button type="primary" icon="el-icon-arrow-left">
        下一页<i class="el-icon-arrow-right el-icon-right"></i>
      </el-button>
    </el-button-group>

    <el-button-group>
      <el-button icon="el-icon-edit" type="primary"></el-button>
      <el-button type="primary" icon="el-icon-share"></el-button>
      <el-button type="primary" icon="el-icon-delete"></el-button>
    </el-button-group>

    <el-button type="success">提交</el-button>
    <el-button :loading="isLoading" icon="el-icon-edit" type="primary" @click="click"></el-button>
    <el-button :disabled="disabled" type="info">提交</el-button>
    <el-button :disabled="disabled" type="warning">提交</el-button> -->
    <!-- <form action="http://www.baidu.com" method="get">
      <el-button @click="doSubmit" type="primary">提交</el-button>
    </form> -->
    <header class="header header-fixed">
      <el-row>
        <el-col :span="24">
          <el-menu class="el-menu-demo" mode="horizontal" default-active="1">
            <el-menu-item index="1">高级插件</el-menu-item>
            <el-menu-item index="2">在线商城</el-menu-item>
            <el-menu-item index="3">客户管理</el-menu-item>
            <el-menu-item index="4">系统设置</el-menu-item>
            <el-menu-item index="5">活动发布</el-menu-item>
          </el-menu>
        </el-col>
      </el-row>
    </header>
    <main>
      <div class="main-left">
        <el-menu class="el-menu-vertical-demo">
          <el-menu-item>活动发布</el-menu-item>
          <el-menu-item>活动管理</el-menu-item>
        </el-menu>
      </div>
      <div class="main-right">
        <div class="activePublic">
          <el-steps :space="200" :active="step">
            <el-step title="活动信息"></el-step>
            <el-step title="报名签到"></el-step>
            <el-step title="分享设置"></el-step>
            <el-step title="个性设置"></el-step>
          </el-steps>
          <div class="step1">
            <el-form class="demo-ruleForm" ref="ruleForm" label-position="top" :model="ruleForm">
              <el-form-item prop="name" label="活动名称">
                <!-- v-model双向数据绑定 -->
                <el-input v-model="ruleForm.name" size="larget"></el-input>
              </el-form-item>
              <el-form-item label="" prop="fenLei">
                <el-row style="height:35px;" type="flex" align="middle">
                  <el-col :span="3" style="width:90px;">
                    <div class="el-form-item__label">活动分类</div>
                  </el-col>
                  <el-col :span="2">
                    <el-button @click.prevent="dialogFormFenLeiVisible=true" type="text">
                      设置
                    </el-button>
                  </el-col>
                </el-row>
                <el-radio-group v-model="ruleForm.fenLei">
                  <el-radio v-for="item of ruleForm.fenLeis" :key="item.name" :label="item.name"></el-radio>
                </el-radio-group>
              </el-form-item>
              <el-form-item>
                <label class="el-form-item__label" for="">活动标签</label>
                <div class="el-form-item__content">
                  <button type="button" class="el-button" style="vertical-align:middle;margin:10px">
                    <i class="el-icon-plus"></i>
                  </button>
                </div>
              </el-form-item>
              <el-form-item>
                <label for="" class="el-form-item__label">活动时间</label>
                <div class="el-form-item__content">
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-date-picker style="width:150px;" v-model="value1" type="date" placeholder="选择日期"></el-date-picker>
                    </div>
                  </div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-time-select style="width:150px;" v-model="value1" 
                      :picker-options="{ start: '08:30', step: '00:15', end: '18:30'}" 
                      placeholder="选择时间"></el-time-select>
                    </div>
                  </div>
                  <div class="el-col el-col-1" style="text-align:center">——</div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-date-picker style="width:150px;" v-model="value1" type="date" placeholder="选择日期"></el-date-picker>
                    </div>
                  </div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-time-select style="width:150px;" v-model="value1" 
                      :picker-options="{ start: '08:30', step: '00:15', end: '18:30'}" 
                      placeholder="选择时间"></el-time-select>
                    </div>
                  </div>
                </div>
              </el-form-item>
              <el-form-item>
                <label for="" class="el-form-item__label">报名时间</label>
                <div class="el-form-item__content">
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-date-picker style="width:150px;" v-model="value1" type="date" placeholder="选择日期"></el-date-picker>
                    </div>
                  </div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-time-select style="width:150px;" v-model="value1" 
                      :picker-options="{ start: '08:30', step: '00:15', end: '18:30'}" 
                      placeholder="选择时间"></el-time-select>
                    </div>
                  </div>
                  <div class="el-col el-col-1" style="text-align:center">——</div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-date-picker style="width:150px;" v-model="value1" type="date" placeholder="选择日期"></el-date-picker>
                    </div>
                  </div>
                  <div class="el-col el-col-5" style="width:20.83333%;">
                    <div class="block" style="text-align:center;">
                      <el-time-select style="width:150px;" v-model="value1" 
                      :picker-options="{ start: '08:30', step: '00:15', end: '18:30'}" 
                      placeholder="选择时间"></el-time-select>
                    </div>
                  </div>
                </div>
              </el-form-item>
              <el-form-item>
                <label for="" class="el-form-item__label">活动地点</label>
                <div class="el-form-item__content">
                  <div class="el-form">
                    <div class="el-row">
                      <div class="el-col el-col-5" style="width:190px;padding:0 20px;">
                        <el-select  placeholder="请选择活动区域">
                          <el-option label="区域一" value="shanghai"></el-option>
                          <el-option label="区域二" value="beijing"></el-option>
                        </el-select>
                      </div>
                      <div class="el-col el-col-5" style="width:190px;padding:0 20px;">
                        <el-select placeholder="请选择活动区域">
                          <el-option label="区域一" value="shanghai"></el-option>
                          <el-option label="区域二" value="beijing"></el-option>
                        </el-select>
                      </div>
                      <div class="el-col el-col-12" style="width:290px;padding:0 20px;">
                        <el-select placeholder="请选择活动区域">
                          <el-option label="区域一" value="shanghai"></el-option>
                          <el-option label="区域二" value="beijing"></el-option>
                        </el-select>
                      </div>
                    </div>
                  </div>
                </div>
              </el-form-item>
            </el-form>
            <el-dialog title="设置活动分类" :visible.sync="dialogFormFenLeiVisible">
              <el-form>
                <el-form-item>
                  <el-tag v-for="fenLei of ruleForm.fenLeis" 
                    type="primary" :key="fenLei.name" @close="handleClose()" closable>{{fenLei.name}}</el-tag>
                </el-form-item>
              </el-form>
            </el-dialog>
          </div>
          <!-- 按钮组 上一步 下一步 发布活动 -->
          <el-button-group>
            <el-button v-show="preStep" @click.native.prevent="handlePreStep">上一步</el-button>
            <el-button v-show="nextStep" type="primary" @click.native.prevent="handleNextStep">下一步</el-button>
            <el-button type="primary">发布活动</el-button>
          </el-button-group>
        </div>
      </div>
    </main>
  </div>
</template>

<script>
// import ElButton from '@/components/ElButton'
// import ElButtonGroup from '@/components/ElButtonGroup'
export default {
  name: 'App',
  data () {
    return {
      disabled: false,
      isLoading: false,
      dialogFormFenLeiVisible: false,
      step: 2,
      preStep: true,
      nextStep: true,
      value1: '',
      ruleForm: {
        name: '',
        fenLeis: [
          {
            name: '未发布'
          },{
            name:'测试活动'
          },{
            name:'精彩活动'
          }
        ],
        fenLei: '测试活动',
        tags: []
      }
    }
  },
  mounted:function() {
    // setTimeout(() => {
    //   this.disabled = true
    // }, 2000);
  },
  components: {
    // 'el-button': ElButton,
    // 'el-button-group': ElButtonGroup
  },
  methods: {
    doSubmit (evt) {
      // this.isLoading = true;
      console.log(evt);
    },
    handlePreStep () {
      this.step--;
      this.goStep(this.step);
    },
    handleNextStep () {
      this.step++;
      this.goStep(this.step);
    },
    goStep(n) {
      switch(n) {
        case 1: this.preStep = false;this.nextStep = true;break;
        case 2: this.preStep = true;this.nextStep = true;break;
        case 3: this.preStep = true;this.nextStep = true;break;
        case 4: this.preStep = true;this.nextStep = false;break
      }
    },
    handleClose () {
      this.dialogFormFenLeiVisible = false
    }
  }
  
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  min-width: 1200px;
  margin: 0 auto;
  font-family: sans-serif;
}
header {
  z-index: 1000;
  min-width: 1200px;
  transition: all 0.5s ease;
  border-top: #fff;
  box-shadow: 0 2px 4px 0 rgba(0,0,0,.12),0 0 6px 0 rgba(0,0,0,.04);
}
header.header-fixed {
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
}
header.el-menu-demo {
  padding-left: 300px!important;
}
main{margin-top:60px;display: -webkit-box;display: -ms-flexbox;display: flex;  min-height: 800px;  border: solid 40px #E9ECF1;  background-color: #FCFCFC;  }
main .main-left{text-align: center;-webkit-box-flex: 0;-ms-flex: 0 0 200px;flex: 0 0 200px;}
main .main-right{-webkit-box-flex:1;-ms-flex:1;flex:1; background-color: #fff; padding: 50px 70px; }
main .el-menu{background-color: transparent!important;}

</style>
