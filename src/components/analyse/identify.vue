<template>
  <div>
    <div class="search-body" style="overflow: visible">
      <Row :gutter='32'>
        <i-col span="4">
          <i-select    filterable placeholder="城市" clearable style="width: 100%">
            <i-option> </i-option>
          </i-select>
        </i-col>
        <i-col span="4">
          <i-select    filterable placeholder="地区" clearable style="width: 100%">
            <i-option     > </i-option>
          </i-select>
        </i-col>
        <i-col span="8">
          <i-select    filterable placeholder="居委会" clearable style="width: 100%">
            <i-option     > </i-option>
          </i-select>
        </i-col>
        <i-col span="2">
          <Button type="success" @click="filterMsg=true">过滤信息</Button>
          <transition name="fade2">
          <div   v-show="filterMsg" style="  width: 500px;position: absolute; left: -250px;padding: 10px;background: #fff;z-index:9;box-shadow: 0 2px 6px rgba(0, 0, 0, 0.117647), 1px 0 1px rgba(0, 0, 0, 0.117647), -1px 0 1px rgba(0, 0, 0, 0.117647)">
            <Checkbox-group v-model="tableColumnsChecked" v-if="true" @on-change="changeTableColumns"  >
              <!--<Checkbox label="sellCount">姓名</Checkbox>-->
              <Checkbox label="weak">性别</Checkbox>
              <Checkbox label="signin">民族</Checkbox>
              <Checkbox label="click">出生年月</Checkbox>
              <Checkbox label="active">地址</Checkbox>
              <Checkbox label="day7">身份证编号</Checkbox>
              <Checkbox label="day30">签发机关</Checkbox>
              <Checkbox label="tomorrow">签发时间</Checkbox>
              <Checkbox label="day">有效截止时间</Checkbox>
              <Checkbox label="week">创建时间</Checkbox>
              <Checkbox label="month">最新认证时间</Checkbox>
              <Checkbox label="month">手机号码</Checkbox>
              <Checkbox label="month">固定电话</Checkbox>
              <Checkbox label="month">行政区全名称</Checkbox>
              <Checkbox label="month">是否有指静脉信息</Checkbox>
              <Checkbox label="month">是否有身份证照片</Checkbox>
              <Checkbox label="month">是否拍摄照片</Checkbox>
              <Checkbox label="month">认证时间</Checkbox>
              <Checkbox label="month">修改日期</Checkbox>
              <Checkbox label="month">是否去世</Checkbox>
              <Checkbox label="month">去世日期</Checkbox>
              <Checkbox label="month">证件类型</Checkbox>
            </Checkbox-group>
            <Row>
              <Button @click="filterOk">确定</Button>
            </Row>
          </div>
          </transition>
        </i-col>
     <!--   <i-col span="4">
          <i-select    filterable placeholder="认证状态" clearable style="width: 100%">
            <i-option     > </i-option>
          </i-select>
        </i-col>-->


        <i-col span="4" >
          <i-button type="info"  >搜索</i-button>
        </i-col>
      </Row>
        <p v-if="!aa" @click="changeAa" style="margin-top: 10px;color: gainsboro;font-size: 14px">  <Icon type= "arrow-down-b"></Icon>展开高级搜索项</p>
      <Row :gutter='32' v-if="aa"   style="margin-top: 10px">
        <i-col span="4">
          <i-select    filterable placeholder="认证状态" clearable style="width: 100%">
            <i-option     > </i-option>
          </i-select>
        </i-col>
        <i-col span="4">
        <Date-picker type="date" placeholder="选择日期" style="width: 200px"></Date-picker>
        </i-col>
      </Row>
    </div>
    <div  >
    <div style=" text-align: right;margin-bottom: 10px; " >
      <Button>打印</Button>
      <!--<Button>导出原始数据</Button>-->
      <Button>数据恢复</Button>
      <Button type="primary" size="large" @click="exportData(2)"><Icon type="ios-download-outline"></Icon> 导出排序和过滤后的数据</Button>
    </div>



    <div  >
    <Table :data="dataCore" :columns="tableColumns2" border stripe   ref="table"></Table>

    </div>

    <Page :total="100" styles="float:right;margin-top:20px"  :current="1" @on-change="changePage"></Page>
    </div>
  </div>
</template>
<script type="text/ecmascript-6">

  export default{
    data () {
      return {
          aa:false,
        dataCore:[],
        filterMsg:false,
        dataCore2:[],
//         tableData2: this.mockTableData2(),
        tableColumns2: [],
//        tableColumnsChecked: ['show', 'weak', 'signin', 'click', 'active', 'day7', 'day30', 'tomorrow']
        tableColumnsChecked:[]
      }
    },

    components: {},
    methods: {
      changeAa(){
          this.aa=true
      },
      filterOk() {
          this.filterMsg=false
      },
//      changePage () {
        // 这里直接更改了模拟的数据，真实使用场景应该从服务端获取数据
//        this.dataCore = this.mockTableData2();
//      },
      getpage () {
        var _this = this;
        _this.$http.get("http://192.168.31.99:8040/remotesite/records?active=2&len=10")
          .then(function (rsp) {
//            console.log(rsp.data.goods.type)
            _this.dataCore=rsp.data
            console.log( rsp.data)
//            _this.dataCore =rsp.data.goods[0].foods

            _this.tableColumnsChecked.push('show', 'weak', 'signin', 'click','active', 'day7', 'day30','tomorrow','month','day')
            _this.tableColumns2 = _this.getTable2Columns();
          })
          .catch(function (error) {
            console.log(error);
          })

      },
      exportData (type) {
         if (type === 2) {
          this.$refs.table.exportCsv({
            filename: '排序和过滤后的数据',
            original: false
          });
        }
      },
    /*  mockTableData2 () {
        let data = [];
        function getNum() {
          return Math.floor(Math.random () * 1000000 + 1);
        }
        for (let i = 0; i < 10; i++) {
          data.push({
            name: '推广名称' + (i+1),
            fav: 0,
            show: getNum(),
            weak: getNum(),
            signin: getNum(),
            click: getNum(),
            active: getNum(),
            day7: getNum(),
            day30: getNum(),
            tomorrow: getNum(),
            day: getNum(),
            week: getNum(),
            month: getNum()
          })
        }
        return data;
      },*/
      getTable2Columns () {
        const table2ColumnList = {
          name: {
            title: '姓名',
            key: 'personName',
            fixed: 'left',
            width: 200
          },
          show: {
            title: '性别',
            key: 'show',
            width: 150,
            sortable: true
          },
          weak: {
            title: '民族',
            key: 'companyName',
            width: 150,
            sortable: true
          },
          signin: {
            title: '出生年月',
            key: 'appID',
            width: 150,
            sortable: true
          },
          click: {
            title: '地址',
            key: 'click',
            width: 150,
            sortable: true
          },
          active: {
            title: '身份证编号',
            key: 'active',
            width: 150,
            sortable: true
          },
          day7: {
            title: '签发机关',
            key: 'day7',
            width: 150,
            sortable: true
          },
          day30: {
            title: '签发时间',
            key: 'day30',
            width: 150,
            sortable: true
          },
          tomorrow: {
            title: '有效截止时间',
            key: 'tomorrow',
            width: 150,
            sortable: true
          },
          day: {
            title: '创建时间',
            key: 'day',
            width: 150,
            sortable: true
          },
          week: {
            title: '最新认证时间',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '手机号码',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '固定电话',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '行政区全名称',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '是否有指静脉信息',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '是否有身份证照',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '是否拍摄照片',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '认证时间',
            key: 'week',
            width: 150,
            sortable: true
          },  week: {
            title: '修改时间',
            key: 'week',
            width: 150,
            sortable: true
          },
          month: {
            title: '是否去世',
            key: 'month',
            width: 82,
            sortable: true
          } ,month: {
            title: '是否去世',
            key: 'month',
            width: 82,
            sortable: true
          } ,month: {
            title: '去世日期',
            key: 'month',
            width: 82,
            sortable: true
          } ,month: {
            title: '证件类型',
            key: 'month',
            width: 120,
            sortable: true
          }
        };

        let data = [table2ColumnList.name];

        this.tableColumnsChecked.forEach(col => data.push(table2ColumnList[col]));

        return data;
      },

      changeTableColumns () {
        this.tableColumns2 = this.getTable2Columns();
      },
      toggleFav (index) {
        this.tableData2[index].fav = this.tableData2[index].fav === 0 ? 1 : 0;
      }
    },
    mounted () {
      this.changeTableColumns();
    },
    created(){
      this.getpage();
    }


  }
</script>
<style>
  .search-body{
    padding-bottom: 0.07rem;
    font-size: 24px;

    height: 50px;
    margin-bottom: 0.16rem;
    font-weight: 400;
    color: rgba(0, 0, 0, 0.87);
    position: relative;
    margin-left: 6px;
  }
  .fade2-enter-active, .fade2-leave-active {
    transition: all .5s ;

  }
  .fade2-enter, .fade2-leave-active {
    opacity: 0;
   height: 0;
    width: 0;
    transform:translateX(180px) rotate(180deg);
  }
</style>
