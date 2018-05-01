<template>
  <div id="main">
    <!-- 这里是YouTube视频插件 -->
    <div class="video">
      <iframe
      class="teaser-video" type="text/html" 
      src="https://www.youtube.com/embed/-8BBKPrjb3A?autoplay=0&amp;origin=https://booc.io&amp;showinfo=0&amp;rel=0"
      frameborder="0">
      </iframe>
    </div>
    <!-- 这里是说明文件 -->
    <div class="main_text">
      <p class="main_text_h1"> {{ main_h1 }}</p>
      <div class="main_text_index">
        <div class="main_text_index_left">
          <p>{{ main_name }}</p>
          <p>{{ main_text }}</p>
          <!-- 跳转路由按钮 -->
          <button @click="tabBook">  
            {{ open }}
          </button>
        </div>
        <div class="main_text_index_right">
          <p>learned</p>
          <p class="main_text_index_right_span">{{name}} of {{number}}</p>
          <p>Concepts</p>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data () {
    return {
      name: '书名字',
      number: '100',
      main_h1: 'Courses',
      main_name: 'Advanced Quantitative Political Methodology',
      main_text: 'Following Gov 2000 or the equivalent course in linear regression, Gov 2001 is the second in the methods sequence for Government Department graduate and undergraduate students.  While not required, most Government graduate students doing empirical work take the course.  Graduate students in other departments and schools at Harvard (and in the area) also take the course. Undergraduates preparing to write quantitative theses are especially welcome to take Gov 1002, which is taught along with this class.  Non-Harvard students and others may also take this course by registering through the Harvard extension school, for course credit or as an auditor (see course number Stat E-200).',
      open: 'Enter Course' 
    }
  },
  methods: {
    tabBook () {
      // 将路由指向book页面
      this.$router.push({path:'/book'})
    }
  }
}
</script>
<style scoped>
/* scoped是这里的css是独立样式的意思 */
#main {
  width: 100%;
  height: 100%;
  text-align: center;
}
.video {
  display: flex;
  justify-content: center;
  margin-top: 20px;
}
.teaser-video {
  width:600px;
  height:338px;
}
.main_text_h1 {
  font-size: 24px;
  margin-top: 20px;
  margin-bottom: 10px;
  margin-right: 1050px;
}
.main_text_index {
  margin: 0 auto;
  width: 1170px;
  height: 228px;
  border-radius: 4px;
  border: 1px solid #ddd;
  display: flex;
}
.main_text_index_left {
  width: 876px;
  padding: 10px;
  text-align: left;
  border-right: 1px solid #ddd;
}
.main_text_index_left p:first-child {
  font-size: 18px;
  margin:15px 0 10px 0;
}
.main_text_index_left p:last-child {
  line-height: 20px;
}
.main_text_index_left button {
  border-color: #245580;
  color: #fff;
  background-image: linear-gradient(to bottom,#337ab7 0,#265a88 100%);
  display: inline-block;
  padding: 6px 12px;
  margin-bottom: 0;
  font-size: 14px;
  font-weight: 400;
  line-height: 1.42857143;
  text-align: center;
  white-space: nowrap;
  vertical-align: middle;
  border-radius: 4px;
  border: 1px solid transparent;
  position: relative;
  top: 20px;
  left: 750px;
}
.main_text_index_right {
  width: 300px;
}
.main_text_index_right p:first-child {
  font-size: 14px;
  margin: 20px;
}
.main_text_index_right p:last-child {
  font-size: 14px;
  margin: 15px;
}
.main_text_index_right_span {
  font-size: 28px;

}
   
</style>
