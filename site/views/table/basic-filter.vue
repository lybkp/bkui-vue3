<template>
  <div class="row">
    <div class="cell">
      <span class="title">默认过滤</span>
      <bk-table
        :columns="columns"
        :data="tableData"
        @dblclick="handleDblClick"
        @column-sort="handleSortBy"
      />
    </div>
    <div
      class="cell"
      style="height: 300px;"
    >
      <span class="title">自定义过滤</span>
      <bk-table
        :columns="columns1"
        :data="tableData"
        height="100%"
        @dblclick="handleDblClick"
      />
    </div>
  </div>
</template>

<script>
  import { defineComponent } from 'vue';

  import { DATA_COLUMNS, DATA_COLUMNS1, DATA_TABLE } from './options';
  export default defineComponent({
    components: {},
    data() {
      return {
        tableData: [...DATA_TABLE],
        columns: [...DATA_COLUMNS],
        columns1: [...DATA_COLUMNS1],
        settings: {
          fields: [],
          checked: [],
        },
      };
    },
    mounted() {
      setTimeout(() => {
        this.settings.checked.push('index');
        this.settings.fields.push(...[{
                                        label: '序号',
                                        field: 'index',
                                        disabled: true,
                                      },
                                      {
                                        label: '名称/内网IP',
                                        field: 'ip',
                                      },
                                      {
                                        label: '来源',
                                        field: 'source',
                                      },
                                      {
                                        label: '创建时间',
                                        field: 'create_time',
                                      }]);
      }, 1000);
    },
    methods: {
      handleSortBy(arg) {
        console.log('handleSortBy', arg);
      },
      handleDblClick(...args) {
        console.log(args);
      },
    },
  });
</script>
<style scoped>
.row {
  display: flex;
  width: 100%;
}

.cell {
  flex: 1;
  margin: 0 5px 0 5px;
}
</style>
