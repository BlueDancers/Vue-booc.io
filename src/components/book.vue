<template>
  <div id="book">
    <div class="book_list">
      <!-- 这里是说明文字 -->
      <div class="book_header">
        <p>Advanced Quantitative</p>
        <p>Political Methodology</p>
        <button @click="tableshow">Learn</button>
      </div>
      <!-- 这里是侧边栏组件  搜索 -->
      <el-input
        placeholder="请输入要学习章节"
        v-model="filterText">
      </el-input>
      <!-- 这里是侧边栏组件树 -->
      <el-tree 
        class="filter-tree"
        :data="data2"
        :props="defaultProps"
        default-expand-all
        :filter-node-method="filterNode"
        @node-click="handleNodeClick"
        ref="tree2">
      </el-tree>
    </div>
     <!-- 这里是组件 默认显示bookmap 由ismap控制 点击上面的按钮 Learn 切换都pdf组件  -->
    <bookmap v-show="ismap"></bookmap>
    <bookpdf v-show="!ismap"></bookpdf>
  </div>
</template>

<script>
import bookpdf from './pdf'
import bookmap from './map'
export default {
  components: {
    bookmap,
    bookpdf
  },
  watch: {
    filterText(val) {
      this.$refs.tree2.filter(val);
    }
  },
  data() {
    return {
      ismap:true,
      filterText: '',
      data2: [{
        id: '1',
        label: '一级 1',
        children: [{
          id: '1-1',
          label: '二级 1-1',
          children: [{
            id: '1-1-1',
            label: '三级 1-1-1'
          }, {
            id: '1-1-2',
            label: '三级 1-1-2'
          }]
        }]
      }, {
        id: '2',
        label: '一级 2',
        children: [{
          id: '2-1',
          label: '二级 2-1'
        }, {
          id: '2-2',
          label: '二级 2-2'
        }]
      }, {
        id: '3',
        label: '一级 3',
        children: [{
          id: '3-1',
          label: '二级 3-1'
        }, {
          id: '3-2',
          label: '二级 3-2'
        }]
      }],
      defaultProps: {
        children: 'children',
        label: 'label'
      }
    }
  },
  methods: {
    filterNode(value, data) {
      console.log(this.filterText)
      if (!value) return true;
        return data.label.indexOf(value) !== -1;
    },
    handleNodeClick(data) {
      console.log(data.id);
    },
    tableshow () {
    this.ismap = !this.ismap
    }
  }
}
</script>

<style>
#book {
  display: flex;
}
.tab {
  display: block;
}
.el-input__inner {
  width: 350px;
}
.el-tree{
  width: 350px;
  display: inline-block;
}
.el-tree-node__content {
  background-color: #eae5e5;
  padding: 5px 0 5px 0;
  -webkit-user-select: none;
}
.el-tree-node__label {
  color: #337ab7;
}
.map {
  width: 1000px;
  height: 800px;
}
.book_list {
  background-color: #eae5e5;
  width: 350px;
}
.book_header {
  font-family: inherit;
  font-weight: 500;
  line-height: 1.1;
  font-size: 24pt;
  width: 350px;
  height: 120px;
  background: #aba6c0;
  padding-top: 20px;
  color: white;
}
.book_header button {
    font-size: 11pt;
    width: 49%;
    float: left;
    height: 26pt;
    margin: 0 1% 5pt 0;
    border-radius: 5pt;
    border: 1px solid #ddd;
    background: #8b87a2;
    display: block;
    color: #edecf1;
    top: 5px;
    padding: 0 2px 0 0;
    text-align: center;
}
.book_header button:hover {
  background: #b8b5d7;
  color: #333;
}
</style>
