<template>
    <div class="content" >
      <div class="module-wrapper">

        <div class="module-header">
          <img src="../images/company-logo.png" alt="" class="module-img"><span class="company-name">西安圣点科技</span>
          <span class="word">社保参保人员指静脉识别一体化系统登录</span> <span class="cover"></span></div>
        <div class="module-content">
          <div class="con-wrapper">
        <i-form ref="formInline" :model="formInline" :rules="ruleInline"  >
          <Form-item prop="user">
            <i-input type="text" size="large"    v-model="formInline.user" placeholder="Username" @keyup.enter.native="handleSubmit('formInline')" autofocus>
              <Icon  style="font-size: 20px;font-weight: 600" type="ios-person-outline" slot="prepend"></Icon>
            </i-input>
          </Form-item>
          <Form-item prop="password">
            <i-input size="large" type="password"  v-model="formInline.password" @keyup.enter.native="handleSubmit('formInline')" placeholder="Password">
              <Icon  style="font-size: 20px;font-weight: 600" type="ios-locked-outline" slot="prepend"></Icon>
            </i-input>
          </Form-item>
          <Form-item>
            <Button type="primary" style="width: 90px;height: 50px" size="large" @click.native="handleSubmit('formInline')" > 登录 </Button>
          </Form-item>
        </i-form>
          </div>
        </div>
      </div>
<!--

        <div style="width: 50%">
          <i-col span="24" class="demo-tabs-style1" style="background: #e3e8ee;padding:16px;">
        <Tabs type="card">
          <Tab-pane label="用户登录">

            <i-form ref="formInline" :model="formInline" :rules="ruleInline"  >
              <Form-item prop="user">
                <i-input type="text" v-model="formInline.user" placeholder="Username" @keyup.enter.native="handleSubmit('formInline')" autofocus>
                <Icon type="ios-person-outline" slot="prepend"></Icon>
                </i-input>
              </Form-item>
              <Form-item prop="password">
                <i-input type="password"  v-model="formInline.password" @keyup.enter.native="handleSubmit('formInline')" placeholder="Password">
                <Icon type="ios-locked-outline" slot="prepend"></Icon>
                </i-input>
              </Form-item>
              <Form-item>
                <Button type="primary" @click.native="handleSubmit('formInline')" > 登录 </Button>
              </Form-item>
            </i-form>
          </Tab-pane>


        </Tabs>
        </i-col>
        </div>
-->



    </div>
</template>
<script type="text/ecmascript-6">

    export default{
        data(){
            return { formInline: {
              user: '',
              password: ''
            },
              ruleInline: {
                user: [
                  { required: true, message: '请填写用户名', trigger: 'blur' }
                ],
                password: [
                  { required: true, message: '请填写密码', trigger: 'blur' },
                  { type: 'string', min: 6, message: '密码长度不能小于6位', trigger: 'blur' }
                ]
              }}
        },
      methods: {
        handleSubmit(name) {
          this.$refs[name].validate((valid) => {
            if (valid) {
              this.$Message.success('提交成功!');
              localStorage.setItem('id_token', '666888999111000222333')
              let arr=['pickUp','acquisition','module']
              this.$router.push({ path: arr[2] })
            } else {
              this.$Message.error('表单验证失败!');
            }
          })
        },
        login(){
            console.log('???????')
        }
      },
        components: {}
    }
</script>
<style scoped>
  body{
    position: relative;
  }
  body {
    height: 100%;
    background: red;
  }
  .content{
    width: 100%;
    height: 100%;
    position: absolute;
    background: url('../images/lou.jpg') no-repeat;
    background-size: cover;
  }
  .demo-tabs-style1 > .ivu-tabs-card > .ivu-tabs-content {
    height: 120px;
    margin-top: -16px;

  }

  .demo-tabs-style1 > .ivu-tabs-card > .ivu-tabs-content > .ivu-tabs-tabpane {
    background: #fff;
    padding: 16px;

  }

  .demo-tabs-style1 > .ivu-tabs.ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab {
    border-color: transparent;
  }

  .demo-tabs-style1 > .ivu-tabs-card > .ivu-tabs-bar .ivu-tabs-tab-active {
    border-color: #fff;
  }
  .demo-tabs-style1{
  box-shadow: 0 9px 30px -6px rgba(0, 0, 0, 0.2), 0 18px 20px -10px rgba(0, 0, 0, 0.4), 0 18px 20px -10px rgba(0, 0, 0, 0.4), 0 10px 20px -10px rgba(0, 0, 0, 0.4);
  }

  .module-wrapper {
    width: 800px;
    height: 500px;

    border-radius: 10px;
    margin: 200px auto;
    position: relative;
    box-shadow: 0 9px 30px -6px rgba(0, 0, 0, 0.2), 0 18px 20px -10px rgba(0, 0, 0, 0.4), 0 18px 20px -10px rgba(0, 0, 0, 0.4), 0 10px 20px -10px rgba(0, 0, 0, 0.4)
  }
  .word{
    position: relative;
    z-index: 999;
  }
  .company-name{
    color: #fff;
    z-index: 999;
    position: absolute;
    font-size: 20px;
    top: -70px;
    left: 50px;
    font-family: cursive;
  }
  .module-img{
    position: absolute;
    left: 10px;
    top: 5px;
    z-index: 999;
    width: 40px;
    height: 40px;
  }

  .module-header{
    border-radius: 5px 5px 0 0;
    overflow: hidden;
    width: 800px;
    height: 200px;
    position: relative;
    color: #fff;
    font-size: 40px;
    line-height: 200px;
    text-align: center;
    background:rgba(0,0,0,.75);

    z-index: 99;
  }
  .module-content{
    height: 300px;
    border-radius: 0 0 5px 5px;
    background: rgba(255,255,255,.955);
text-align: center;

  }
  .con-wrapper{
    width: 50%;
margin-left: 25%;
    padding-top: 80px;
  }

</style>
