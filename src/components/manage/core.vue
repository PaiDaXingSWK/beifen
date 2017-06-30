<template>
    <div>
      <div class="content-header">
        所有设备
        <span>
      <Button type="info" icon='plus' @click='showIncrease = true' size="small"></Button>
        </span>
      </div>
      <div style="text-align: right;margin-bottom: 10px">
        <Button>数据备份</Button>
        <Button>数据恢复</Button>
      </div>
      <Table border :columns="columnsCore" :row-class-name="rowClassName" :data="dataCore"></Table>
    </div>
</template>
<script type="text/ecmascript-6">

    export default{
        data(){
            return {
              columnsCore: [
                {
                  title: '名称',
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
                  title: '类型',
                  key: 'type'
                },
                {
                  title: '状态',
                  key: 'status',
                  render: (h, params) => {
                    const row = params.row;
                    const color = row.status === 1 ? 'blue' : row.status === 2 ? 'green' : 'red';
                    const text = row.status === 1 ? '构建中' : row.status === 2 ? '构建完成' : '设备异常';

                    return h('Tag', {
                      props: {
                        type: 'dot',
                        color: color
                      }
                    }, text);
                  }
                },
                 {
                  title: 'ip',
                  key: 'ip'
                }, {
                  title: '型号',
                  key: 'num'
                },
                {
                  title: '操作',
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
                      }, '查看'),
                      h('Button', {
                        props: {
                          type: 'error',
                          size: 'small'
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
              dataCore: [

              ]
            }
        },
        components: {},
      methods:{
        getpage () {
          var _this = this;
          _this.$http.get("./static/data.json")
            .then(function (rsp) {
              console.log(rsp.data.goods.type)
              _this.dataCore=rsp.data.goods
              _this.dataCore.name=rsp.data.goods[0].foods
            })
            .catch(function (error) {
              console.log(error);
            })
        },
        rowClassName (row, index) {
          if (row.type === -1) {
            return 'aa';
          } else if (row.type === 2) {
            return 'demo-table-error-row';

          }
          return '';
        }
      },
      created(){
        this.getpage();

      }
    }
</script>
<style>
  .ivu-table .demo-table-info-row td{
    background-color: #2db7f5;
    color: #fff;
  }
  .ivu-table .demo-table-error-row td{
    background-color: lightsalmon;
    color: #fff;
  }

</style>
