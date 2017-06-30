<template>
  <div style="width: 100%">
   <!--<v-peopleList></v-peopleList>-->

    <div class="list-content" style="box-shadow: 2px 10px 18px #333333;">

      <i-menu theme="dark" active-name="1">

        <Menu-item name="1">
          <Icon type="document-text"></Icon>
          人员信息
        </Menu-item>
        <!--  <Menu-item name="2">
            <Icon type="chatbubbles"></Icon>
            管理设置
          </Menu-item>-->

        <!-- <Menu-item name="3">
           <Icon type="heart"></Icon>
           系统恢复
         </Menu-item>
         <Menu-item name="4">
           <Icon type="heart-broken"></Icon>
           系统备份
         </Menu-item>
         <Menu-item name="5">
           <Icon type="heart-broken"></Icon>
           参数配置
         </Menu-item>-->

      </i-menu>
    <!--  <div class="company" @click="comMsg">
        <img width="30px" src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAHgAAAB4CAMAAAAOusbgAAAAGXRFWHRTb2Z0d2FyZQBBZG9iZSBJbWFnZVJlYWR5ccllPAAAAyJpVFh0WE1MOmNvbS5hZG9iZS54bXAAAAAAADw/eHBhY2tldCBiZWdpbj0i77u/IiBpZD0iVzVNME1wQ2VoaUh6cmVTek5UY3prYzlkIj8+IDx4OnhtcG1ldGEgeG1sbnM6eD0iYWRvYmU6bnM6bWV0YS8iIHg6eG1wdGs9IkFkb2JlIFhNUCBDb3JlIDUuMy1jMDExIDY2LjE0NTY2MSwgMjAxMi8wMi8wNi0xNDo1NjoyNyAgICAgICAgIj4gPHJkZjpSREYgeG1sbnM6cmRmPSJodHRwOi8vd3d3LnczLm9yZy8xOTk5LzAyLzIyLXJkZi1zeW50YXgtbnMjIj4gPHJkZjpEZXNjcmlwdGlvbiByZGY6YWJvdXQ9IiIgeG1sbnM6eG1wPSJodHRwOi8vbnMuYWRvYmUuY29tL3hhcC8xLjAvIiB4bWxuczp4bXBNTT0iaHR0cDovL25zLmFkb2JlLmNvbS94YXAvMS4wL21tLyIgeG1sbnM6c3RSZWY9Imh0dHA6Ly9ucy5hZG9iZS5jb20veGFwLzEuMC9zVHlwZS9SZXNvdXJjZVJlZiMiIHhtcDpDcmVhdG9yVG9vbD0iQWRvYmUgUGhvdG9zaG9wIENTNiAoV2luZG93cykiIHhtcE1NOkluc3RhbmNlSUQ9InhtcC5paWQ6MzRFQTI4M0Y3RkFBMTFFNjgwN0Y4RTkwNDZCOUJEQ0QiIHhtcE1NOkRvY3VtZW50SUQ9InhtcC5kaWQ6MzRFQTI4NDA3RkFBMTFFNjgwN0Y4RTkwNDZCOUJEQ0QiPiA8eG1wTU06RGVyaXZlZEZyb20gc3RSZWY6aW5zdGFuY2VJRD0ieG1wLmlpZDozNEVBMjgzRDdGQUExMUU2ODA3RjhFOTA0NkI5QkRDRCIgc3RSZWY6ZG9jdW1lbnRJRD0ieG1wLmRpZDozNEVBMjgzRTdGQUExMUU2ODA3RjhFOTA0NkI5QkRDRCIvPiA8L3JkZjpEZXNjcmlwdGlvbj4gPC9yZGY6UkRGPiA8L3g6eG1wbWV0YT4gPD94cGFja2V0IGVuZD0iciI/PrnUQqkAAAMAUExURd7l+eXp/s7V5vH1+ODm+uDh5eTn8d7h6uHj7vn6/ejp8d7i8vHx8t3d5enx/vLy9ufp7uHp+dTg8+zs7+fn6+zz9+3u9/z8/OHp/d/i9uDi7eLo7u3t8N7f89/k6PDx9vDx9Nri9dLX7erw9/j4+PX0+N7d6eXm79Te6uDt/urq79/r9ejv/t7i7N/k9d7i9Onr/tre69vp/t7g7NHa7t7l8tLU2O3u8+Hj7t/i8N7g5/D1/u7z+M/X7tLU2uTm+/v8//T09eTs/t/m/97g8Pf4+vT2+enp7d/k9+Hj89Xb8tLd68/W9fDz9ubu/uns/ebs/ufp8uLo9uDl/uTk7+Xm6OXk6OLi8ePl6N3j9dzj8t7g8+Dj593j797h7t7e4fv8/e/v8+Xu/u3u8eHm9eXn6+Hk6dvh+eDj697i587V8M/T6/7+/vr6+/////f3+fz7+/f2+Pv7+/X19vn5+/f3+Pb2+Pb29/j4+vPz9vX19/v6+/z8/tzo/vb2+fj5+87T7/r5+fr5+vr6+t3j7PLy887V7eHh6t7k8ePt9s7U6ufo6trk5t7f7/n5+unt/vHx9uDl/PLy9Pj3+Nvl/eXm9ODh9M/W7fv//9/o/d/l/fX09uLm8+Hn8uLm8fPz9OLk987V7ubq8PPz/szv/+jw/uvs7+P7/t7h8Oju9eDf6uzr9fb1993h4OXk5vDv9u7t79Ll/Pr7/Nnb4Nrf4LfQ4f39/fz7/Mfa7dTf49jl9djn3dvj697j9tvk6d/h9qTC2uLh4fb2++Hl5u/w8eHh7eDg79/j89Xd5uLi7szR5Onn+Ofs89XX2vL09evt/uru/eLj6evq7PDw8eLi56anxd3j++Hn/uPo/s3d0N/k79zr/t7q/93l/N/k/+jp9PT19uTo+vT1+Obm6OXl7H2oxeDk8eHo8eDm8djj8ePk8d3i5d7g5OTo99zk8dzk8+bu9fLy9dLd7/Py9ODm9uvs88/R1OLn9eLn+Ozp+tLZ5+vz+OHm6+7t/v38/P///2br04gAAAEAdFJOU////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////wBT9wclAAAGE0lEQVR42uyaeVwUVRzAkUM/AiKEcgiBGAkpCJblBkJEgFpGolBWlkZ5zx7tAgsrckgKqcBqQYfdpd1lVlh2n2S32WG32X1fWpb0xmV3Z957O/Nm5g3x+qP9feAPfvPe+/KbefN7v2MC+P9IAvxgP9gP9oP/B+CI4LAyB+iX6Hee9epMpkEGc0mL9wCPpD2VzYn6wQVfcnIdEKjfMLvV3L17VnuplqwMZs943F2CrWDfk+w2V09ruM2Ljd2Zy2xXcz+J1q4MYfg6JYhYYJnD8D3uhVwDx86BcBdD7rkMPVcRxJ4KGLrMEZCb/AY7X81FQm4aw0OCs0HudSxPJ4gFkSyPRWQ7J3MMwX2I22AZCCxDbnQnQ3Awwu1jGPrUI9zLWMZcDsi9kWWwNx4x+E2G4EKEO59leGuB3DEs4+oLEIM5lmCE+wTLTKIbcscyTWEQgytZgpdC7iKmSRticC5L8B2Q+wXTNLUagk9hCf4acicwTcznszMYByNbi2kp4qxBSxtUwEdDcCFTcDkERz32/vCXJ09+6PWX0tPTN2x4NOnB/Pz8k9zyx2twRtIP8yrWrx91dkXFKBV5+/P7FhDB90Dw5UBBTvdsiFhQAqiklADmAB14R3EHHbiNAIZ1DrD/F6UFznBzv1wJKGUpAQyTw5EPAFVw4JlWWnAiAdwqjhhqSlBa4Kh+g5++E1ALJw+OhmD+NqX5v7kGb+8opgcvlAfDARfy/DEK8//uHzx6Pz34RzXwIZ6//ZEpeYGB4wTNVcub1q1ralq7Ni/v5hXuwaPh8PtD62ocDebaWqPR9eMRi+u3ttZsNpoR8J9q4F2C6iOi6wbTGoVz7FYVHwXP2l418HcawEAA/8NrBrepge8WVBsRMF4aduXNaNCvVDa2a7c4RgN4mhc8Q/U4sGkHdwmquV7FpZLSjLi5ulXBMPmcpPkZawC3q4JTxXUPqIENgmqVV2GTbq7DXgdyDqY2mTIKcktLZ88urCwdUmCSvqZyYJgmZmoAG6s8l17Ei0Xbwq8QKvnWzdFv4YdelDx4qzhgpqA6nnSrXWZ4z4gTefkYxi3hLt1nqr56njjgU51gDsiAD8lHkAj4e+mIVQrgKunrNNUX3F8jyxL/uogAThgoOBPIgQ3yBQb50Ocrr+o09Vsdj78Wzc0YGdvUvaRgT+xngWG6wEW9KSnt7efHv4qCEXMySOBh4pAWDeAqqTfyyuGgYgiGi1YTw1skSc0eCBgElUDwdKlbkoCRUmKYR3Mt2YEIYIP00vYg5FYTols8aav2rRUvUQBbSTWpWDARgsMguJ4Mhs8DXO+56v3LQbYYgL0FKHvLlcno62QhFZEw8Bw4JdqteE8LGIC6uk12+5o1TqfdbsfepshJxDowsRThdujvCisr3GolcZqJZUIcvBPg/m0JETzc2kgX2h5ULL6gXr7/yidkix+mjKv3Kte5bsDd3VwieGGJhYprpCgpunZDCnFzuQZSmfyMGtiA5VgRQsdaJpSy7qPJy1WLqNhZzkekyiSYYnzVN1YJNRIoVqAVC+WRfGBg3qxZy1dMkQ0fr/7w2zZnnaOm5lizucYlZpc0mB3mWqdzZNk1H6P/hJbWQAsy4Tz9VZ041OC/tICj0BmZernZ6Cph2to/reicjSqJEUFi0DVsWhteRnTWCXrsbdiGLlGoFYxHqR/oqNoB9ccl29Rsw48YWi4ebaZp7y1irQk5P6soGQexuc/zNGC+CydTPOiZCiUmDWDO1ykd0IbdEuozr4enA0vToEUxGrg5vrOCeVow/0qq7yKhccrUzm7fGc3P8fRgvlOSggFbDrnNuXu6ZPiOibweMBZ0wrpMb3C9ZOCQonLpyI6tdN1UVLLkD7zokAUhib9aQY91U+LunJwJ8qPG8PrBPFcN9Ira8aLyIRmXpg/boNpNUf10btdqHdzH6fvHMkYbaLFTj+P/DTDPN0bSYDcbdHXM5SVqqFZscry+xjX5ho/4XUPXZfEtejvmSnLTCy2K1NCfaT7foPzMeVlFuPx+Gl8+oI65FqkMyOpCcm9zWduMOB1fqvi/ofeD/WA/2A/WLEcEGACyiT5VLFIw3AAAAABJRU5ErkJggg==" alt="">
        <br>
        <span class="company-name">
         圣点科技提供技术支持
        </span>
      </div>-->

    </div>
    <div class="content">
      <Modal
        v-model="addPerson"
        title="普通的Modal对话框标题"
        @on-ok="ok2('user2')"
        @on-cancel="cancel">
        <Select v-model="user2.name" size="small" style="width:100px">
          <Option v-for="item in com" :value="item.name" :key="item.id">{{ item.name }}</Option>
        </Select>
      </Modal>

      <Row>
        <div class="content-header">
          人员信息
          <span>
      <Button type="info" icon='plus' @click='showIncrease = true;addPerson=true' size="small"></Button>
        </span>
        </div>
        <div class="oparity">
          <!-- <ul>
             <li @click="massageGathers">信息采集</li>
             <li @click="peopleShowOnoff">照片采集</li>
             <li  @click="modal1 = true">指静脉采集</li>
           </ul>-->
          <div v-if="peopleShow">
            <img src="../../assets/logo.png" alt="">
            <img src="../../assets/logo.png" alt="">
          </div>
        </div>
      </Row>
      <router-view></router-view>
      <v-peopleMsg v-show="peopleShow"></v-peopleMsg>

      <!--显示的第二张方案-->



         <div class="search-body" style="overflow: visible">

          <Row :gutter='32'>
            <i-col span="5">
              <i-input v-model="value" placeholder="请输入姓名" style="width: 300px"></i-input>
            </i-col>
            <i-col span="5">
              <i-input v-model="value" placeholder="请输入身份证号码" style="width: 300px"></i-input>
            </i-col>
            <i-col span="5">
              <i-input v-model="value" placeholder="请输入身社保号码" style="width: 300px"></i-input>
            </i-col>
            <i-col span="1" >
              <i-button type="info" @click="search" size="large">搜索</i-button>
            </i-col>
          </Row>
            <div class="more-search" v-show="aa">
              <Row :gutter='32'>
              <i-col span="7">
                <Cascader :data="data2" placeholder="请选择地区"></Cascader>
              </i-col>

              <i-col span="2">
                <i-select  :model.sync="personMsg.personsex"  filterable placeholder="性别" clearable style="width: 100%">
                  <i-option     > </i-option>
                </i-select>
              </i-col>
              <i-col span="4">
                <date-picker :model.sync="personMsg.time" type="datetime"   placeholder="时间" style="width: 100%"  ></date-picker>
              </i-col>
                <i-col span="2">
                  <i-select  :model.sync="personMsg.personsex"  filterable placeholder="认证状态" clearable style="width: 100%">
                    <i-option     > </i-option>
                  </i-select>
                </i-col>
              </Row>
            </div>
            <p class="search-tip" @click="changeAa" v-show="!aa">
              <Icon type= "arrow-down-b"></Icon>  展开高级查询项
            </p>
 <!-- <p class="search-tip" v-show="!aa">
              <Icon type= "arrow-down-b"></Icon>  展开高级查询项
            </p>-->


        </div>
      <div  style="margin-top: 30px">
        <Table v-show="true" border :columns="columns7" :row-class-name="rowClassName"    :data="data6"></Table>
        <div class="all-btn">
          <ul>
            <li><ol v-if="true">
              <li><Button disabled="disable" size="large" type="error">删除</Button>
                <Button disabled size="large" type="warning">修改</Button></li>
            </ol>
              <ol v-if="false">
              <li><Button   size="large" type="error">删除</Button>
                <Button   size="large" type="warning">修改</Button></li>
            </ol></li>
            <li>  <Page :total="100"></Page></li>
          </ul>


        </div>
      </div>
      <div style="margin-top: 300px">
        <h4 class="com-name">
          西安圣点世纪科技有限公司提供技术支持
        </h4>
        <ul class="com-list">
          <li>
            全国统一客服电话：4006823334
          </li><li>
          技术支持电话：029-88746641
        </li><li>
          公司网站：www.sdkj.com
        </li><li>
          公司地址：西安市高新区高新四路郎臣大厦2103室
        </li><li>
          版本号：0.0.1
        </li>
        </ul>
      </div>


      <!--   <div style="margin-left: 70%">
           <Button>迁移</Button>
           <Button type="primary">读取身份证</Button>
           <Button type="ghost">认证</Button>
           <Button type="error">删除用户</Button>
         </div>-->
      <!-- 拍照 -->
      <!-- <Modal id="takePhote"  width="450"
        v-model="modalPhoto"
        title="普通的Modal对话框标题"
              footer="000"
        @on-ok="ok"
        @on-cancel="cancel">
        <div style="width: 800px"></div>
       <div class="photo-wrapper">
        <v-photo @upup="change"></v-photo>
       </div>
         <div slot="footer" class="aa">

         </div>
      </Modal>-->
      <!--   最新拍照 -->
      <Modal id="takePhote"  width="450"
             v-model="modalPhoto"
             title="普通的Modal对话框标题"
             footer="000"
             @on-ok="ok"
             @on-cancel="cancel">
        <div style="width: 800px"></div>
        <div class="photo-wrapper">
          <div >
            <div class="booth">
              <div class="btn">
                <Button type="success" id="readyw" @click="on">打开摄像头</Button>
                <Button type="success" id="off">关闭摄像头</Button>
              </div>
              <video id="video" width="400" height="300"></video>
              <Button id='tack' type="primary" @click="go"> 拍照</Button>
              <Button id='repeat' type="primary" @click="re"> 重新拍照</Button>
              <canvas id='canvas' width='400' height='300'></canvas>
              <img id='img' src=''>
            </div>

          </div>
        </div>
        <div slot="footer">
          <i-button type="success" @click="submitPhoto('user')">确定</i-button>
          <i-button type="ghost" @click="cancelPhote('user')" style="margin-left: 8px">取消</i-button>
        </div>
      </Modal>
     <!-- <div style="width: 800px;height: 600px;border: 1px solid red;position: absolute;z-index: 9;left: 20%;background: #fff;">
        <div style="height: 50px"></div>
        <v-photo></v-photo>

      </div>-->

      <Modal
        v-model="massageGather"
        title="信息采集"
        @on-ok="photoOk"
        @on-cancel="cancel">
        <p>对话框内容</p>
        <p>对话框内容</p>
        <p>对话框内容</p>
      </Modal>
      <Modal
        v-model="modal1" width='750'
        title="指静脉采集"
        @on-ok="ok"
        @on-cancel="cancel">
        <div>
          <Steps :current="1">
            <Step title="采集准备" content="请选择要采集的手指和用于采集设备"></Step>
            <Step title="采集中" content="进行三次指静脉采集"></Step>
            <Step title="采集完成" content="采集完成"></Step>
          </Steps>
        </div>
        <Row :gutter="32">
          <i-col span="8" push='2'>
            <label>采集设备</label>
          </i-col>
          <i-col span="12">
            <label>采集手指</label>
          </i-col>
        </Row>
        <Row :gutter="32" justify='center'>
          <i-col span="8" push='2'>
            <i-select style='width:134px'>
              <i-option v-for="item in cityList" :value="item.value" :key="item"> {{ item.label }}</i-option>
            </i-select>
          </i-col>
          <i-col span="12">
            <Radio-group type="button">
              <Radio value="l2">左手食指</Radio>
              <Radio value="l3">左手中指</Radio>
              <Radio value="r2">右手食指</Radio>
              <Radio value="r3">右手中指</Radio>
            </Radio-group>
          </i-col>
        </Row>
      </Modal>

    </div>


  </div>
</template>
<script type="text/ecmascript-6">
  import peopleList from '../peopleList.vue'
  import peopleMsg from '../peopleMsg.vue'

//  import photo from '../photo.vue'
  export default{
    data(){
      return {
          aa:false,
        user2: {
          name: ''

        },
          com:'',
        addPerson:false,
        data2: [{
          value: 'zhejiang',
          label: '陕西',
          children: [{
            value: 'hangzhou',
            label: '西安',
            children: [{
              value: 'xihu',
              label: '高新',
              children: [{
                value: 'xihu',
                label: '第一个街道办事处',
                children: [{
                  value: 'xihu',
                  label: '第一个社区居委会'
                }]
              }]
            }]
          }]
        }, {
          value: 'jiangsu',
          label: '江苏',
          disabled: true,
          children: [{
            value: 'nanjing',
            label: '南京',
            children: [{
              value: 'zhonghuamen',
              label: '中华门'
            }]
          }]
        }
        ],
        personMsg: {
          personname: '',
          personid: '',
          personsex: '',
          time: '',
          active: 1,
          len: 50
        },
        massageGather: false,
        modalPhoto:false,
        modal1: false,
        cityList: [
          {
            value: 'beijing',
            label: '北京市'
          },
          {
            value: 'shanghai',
            label: '上海市'
          },
          {
            value: 'shenzhen',
            label: '深圳市'
          },
          {
            value: 'hangzhou',
            label: '杭州市'
          },
          {
            value: 'nanjing',
            label: '南京市'
          },
          {
            value: 'chongqing',
            label: '重庆市'
          }
        ],
        columns7: [
          {
            type: 'selection',
            width: 60,
            align: 'center'
          },
          {
            title: '姓名',
            key: 'name',
            render: (h, params) => {
              return h('div', [
                h('Icon', {
                  props: {
                    type: 'person'
                  }
                }),
                h('strong', params.row.name)
              ]);
            }
          },
          {
            title: '年龄',
            key: 'type'
          },  {
            title: '指静脉信息',
            key: 'type'
          },
          {
            title: '地址',
            key: 'address'
          }, {
            title: '认证时间',
            key: 'address'
          },
          {
            title: '指静脉操作',
            key: 'action',
            width: 150,
            align: 'center',
             render: (h, params) => {
              return h('div', [
                h('Button', {
                  props: {
                    type: 'primary',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.show(params.index)
                    }
                  }
                }, '采集'),
                h('Button', {
                  props: {
                    type: 'error',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.remove(params.index)
                    }
                  }
                }, '删除'),


              ]);
            }
          },
          {
            title: '人员操作',
            key: 'action',
            width: 400,
            align: 'center',
            render: (h, params) => {
              return h('div', [
                h('Button', {
                  props: {
                    type: 'primary',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.show(params.index)
                    }
                  }
                }, '查看'),

                h('Button', {
                  props: {
                    type: 'error',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.remove(params.index)
                    }
                  }
                }, '认证'), h('Button', {
                  props: {
                    type: 'warning',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.camera(params.index)
                    }
                  }
                }, '照片采集') ,
                h('Button', {
                  props: {
                    type: 'info',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.remove(params.index)
                    }
                  }
                }, '修改'),
             /*   h('Button', {
                  props: {
                    type: 'error',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.remove(params.index)
                    }
                  }
                }, '读取身份证'),*/
                h('Button', {
                  props: {
                    type: 'error',
                    size: 'small'
                  },
                  style: {
                    marginRight: '5px'
                  },
                  on: {
                    click: () => {
                      this.remove(params.index)
                    }
                  }
                }, '删除')
              ]);
            }
          }
        ],
        data6: []


      }
    },
    methods: {
      changeAa(){
          this.aa=true
      },
      getpage () {
        var _this = this;
        _this.$http.get('http://192.168.31.99:8040/organizations').then(function(res){

          _this.com=res.data
        })
        _this.$http.get("./static/data.json")
          .then(function (rsp) {
            console.log(rsp.data.goods.type)
            _this.data6=rsp.data.goods
            _this.data6.address=rsp.data.goods[0].foods
          })
          .catch(function (error) {
            console.log(error);
          })
      },
      rowClassName (row, index) {
        if (row.type===2 ) {
          return 'demo-table-error-row';
        } else if (row.type === -1) {
          return 'aaa ';
        }
        return '';
      },
      on(){
          /* 拍照 */
        let   vendorUrl = window.URL || window.webkitURL;
        navigator.getMedia = navigator.getUserMedia ||
          navagator.webkitGetUserMedia ||
          navigator.mozGetUserMedia ||
          navigator.msGetUserMedia;
        navigator.getMedia({
          video: true, //使用摄像头对象
          audio: false  //不适用音频
        }, function(strem){
          console.log(strem);
          video.src = vendorUrl.createObjectURL(strem);
          video.play();
        }, function(error) {
          //error.code
          console.log(error);
        });
      },
      go(){
        /* 拍照 */
        let video = document.getElementById('video');
        let  canvas = document.getElementById('canvas');
        let  snap = document.getElementById('tack');
        let  img = document.getElementById('img');
        //绘制canvas图形
        canvas.getContext('2d').drawImage(video, 0, 0, 400, 300);

        //把canvas图像转为img图片
        img.src = canvas.toDataURL("image/png");

      },
      re(){
        /* 拍照 */
        let  canvas = document.getElementById('canvas');

        let  img = document.getElementById('img');
        canvas.getContext('2d').clearRect(0,0,400,300);
        img.src = canvas.toDataURL("");
      },
      cancelPhote(){
        let  canvas = document.getElementById('canvas');

        let  img = document.getElementById('img');
        canvas.getContext('2d').clearRect(0,0,400,300);
        img.src = canvas.toDataURL("");
        this.modalPhoto=false;
      },
      submitPhoto(){
        let  canvas = document.getElementById('canvas');

        let  img = document.getElementById('img');
        canvas.getContext('2d').clearRect(0,0,400,300);
        img.src = canvas.toDataURL("");
        this.modalPhoto=false;
        this.$Notice.open({
          title: '这是通知标题',
           desc: '这里是通知描述这里,是通知描述这里是通知描述这里,是通知描述这里,是通知描述这里是通知描述这里是通知描述'
        });
      },
      photoOk(){
         $('.booth').css('display','none')
      },
      massageGathers() {
        this.massageGather = true
      },
      ok () {
        this.$Message.info('点击了确定');
      },  ok2 () {
          console.log('++++')
       console.log(this.user2);
      },
      cancel () {
        this.$Message.info('点击了取消');
      },
      camera () {
      this.modalPhoto=true;
            console.log('+++')
       /* this.$Modal.confirm({
          title: '确认对话框标题',
          content: '<div style="width: 800px"></div> <div class="photo-wrapper"> <v-photo></v-photo> </div>',
          okText: '',
          cancelText: 'Cancel'
        });*/
      },
      search(){
          console.log(this.personMsg)
      }

    },
    components: {
      'v-peopleList': peopleList,
      'v-peopleMsg': peopleMsg,

      /*,
      'v-photo': photo*/
    },
    created(){
      this.getpage();
this. rowClassName();
    }
  }
</script>
<style scoped>

  .ivu-table .demo-table-error-row td{
    background-color: red !important;
    color: #fff;
  }
  .content {
    display: flex;
    text-align: center;
    overflow: hidden;
    flex-direction: column;
   /* width: 98.5%;*/
     width: 85.5%;
     margin-left: 260px;
    /*margin: 0 15px 0 15px;*/
    background: #fff;

    box-shadow: 0 2px 6px rgba(0, 0, 0, 0.117647), 1px 0 1px rgba(0, 0, 0, 0.117647), -1px 0 1px rgba(0, 0, 0, 0.117647);
    padding: 20px;
    min-height: 600px;
    margin-bottom: 10px;
    position: absolute;
    bottom: 0;
    top: 90px;
    border-radius: 5px;
  }

  .content-header {
    float: left;
  }

  .oparity {

    text-align: center;

    flex-direction: column;
    width: 71%;
    margin-left: 332px;

    padding: 20px;
  }

  .oparity ul li {
    margin-bottom: 50px;
    list-style: none;
    cursor: pointer;
    display: inline-block;
    float: left;
    width: 150px;
    height: 50px;
    background: dodgerblue;
    margin-left: 10px;
    text-align: center;
    line-height: 50px;
    color: #fff;
  }

  .oparity ul li:hover {
    background: #fff;
    border: 1px solid dodgerblue;
    color: dodgerblue;
  }
  .photo-wrapper{
     width: 200px;height: 400px;
    margin-bottom: 20px;
  }
  .btn{
    margin-bottom: 5px;
  }
  .booth {
    width:420px;

    background:#ccc;
    border: 10px solid #ddd;
    margin: 0 auto;
  }
  #video{
    position: relative;
  }
  img,canvas{
    position: absolute;
    top: 114px;
    left: 26px;
  }
  .search-body{
    padding-bottom: 0.07rem;
    font-size: 24px;

    height: 50px;
    margin-bottom: 0.16rem;
    font-weight: 400;
    color: rgba(0, 0, 0, 0.87);
    position: relative;
    margin-left: 56px;
  }
  .more-search{
    margin-top: 10px;
    margin-left: 0px;
  }
  .search-tip{
    color: gainsboro;
    font-size: 16px;
    float: left;
    margin-left: 20px;
    margin-top: 5px;
    cursor: pointer;
    transition: .5s;
  }
  .search-tip:hover{
    color: #ccc;
  }
  .all-btn{
    float: right;
    margin-top: 20px;
  }
  .all-btn ul li {
    float: left;
    margin-right: 50px;
  }
  .com-name{
    height: 40px;
    line-height: 40px;
    text-align: center;
    font-size: 25px;
    margin-bottom: 20px;
    color: #ebebeb;
  }
  .com-list{
    height: 200px;
  }
  .com-list li{
    line-height: 40px;
    font-size: 14px;
    text-align: center;
    color: #ebebeb;
  }
  .list-content {
    position: absolute;
    top: 70px;
    left: 0;
    bottom: 0;
    background: #1c2438;
    margin-bottom: 10px;
  }

</style>
