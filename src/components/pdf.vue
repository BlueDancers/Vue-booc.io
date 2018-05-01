<template>
	<div id="pdf">
    <div class="pdfbuttom">
    <!-- 是否显示 -->
      <input type="checkbox" v-model="show">
      <!-- 按钮组件 -->
      <el-button-group>
        <el-button type="primary" icon="el-icon-arrow-left" @click="red">上一页</el-button>
        <el-button type="primary" @click="add">下一页<i class="el-icon-arrow-right el-icon--right"></i></el-button>
      </el-button-group>
      <!-- 显示页码 -->
      {{page}} /{{numPages}}
        <el-button @click="rotate += 90">&#x27F3;</el-button>
        <el-button  @click="rotate -= 90">&#x27F2;</el-button>
      <el-button type="info" @click="$refs.pdf.print()">打印</el-button>
    </div>
    <!-- 这里是显示pdf的地方 --> 
		<div class="showpdf">
			<pdf v-if="show" ref="pdf" :src="src" class="pdfbook" :page="page" :rotate="rotate" @password="password" @progress="loadedRatio = $event" @error="error" @num-pages="numPages = $event"></pdf>
		</div>
	</div>
</template>
<script>
import pdf from 'vue-pdf'
export default {
	components: {
		pdf: pdf
	},
	data () {
		return {
			show: true,
			src:'../static/docker.pdf',
			loadedRatio: 0,
			page: 1,
			numPages: 0,
			rotate: 0,
		}
	},
	methods: {
		password: function(updatePassword, reason) {
			updatePassword(prompt('password is "test"'));
		},
		error: function(err) {
			console.log(err);
		},
    red () {
      this.page = this.page-1
    },
    add () {
      this.page = this.page+1
    }
	}
}
</script>

<style>
#pdf {
  width: 1000px;
}
.pdfbook {
  border: 1px solid red
}
.showpdf {
  width: 50%;
  margin: 0 auto;
}
.pdfbuttom {
  position: relative;
  left: 250px;
}
</style>
