<template>
  <div id="app">
    <div class="header">
      <p class="header_left_one" @click="App">BOOC.IO</p>
      <a class="header_left_two" @click="App">IEEE Vis 2016论文</a>
        <a class="header_right_two">Feedback</a>
        <a class="header_right_one">Log In /Sign UP</a>
    </div>
    <router-view/>
  </div>
</template>

<script>
export default {
  methods: {
    App () {
      this.$router.push({ path: '/' })
    }
  }
}
</script>

<style>
#app {
  height: 800px;
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
}
.header {
  background: rgb(104, 100, 127);
  width: 100%;
  height: 51px;
  color: white;
}
.header_left_one { 
  display: inline-block;
  line-height: 52px;
  padding-left: 17px;
  font-size: 18px;
}
.header_left_two {
  display: inline-block;
  margin-left: 10px;
  font-size: 14px;
  line-height: 48px;
  padding: 3px 20px 0px 25px;
  cursor: pointer;
  background: #83809b!important;
  color: white;
}
.header_right_one {
  float: right;
  padding: 3px 20px 0px 25px;
  line-height: 48px;
  border-left: 1px solid #524e72;
}
.header_right_two {
  float: right;
  padding: 3px 20px 0px 25px;
  line-height: 48px;
  border-left: 1px solid #524e72;
}
.header_right_two:hover,.header_right_one:hover  {
  background: #83809b;
}
html, body, div, span, applet, object, iframe,
h1, h2, h3, h4, h5, h6, p, blockquote, pre,
a, abbr, acronym, address, big, cite, code,
del, dfn, em, img, ins, kbd, q, s, samp,
small, strike, strong, sub, sup, tt, var,
b, u, i, center,
dl, dt, dd, ol, ul, li,
fieldset, form, label, legend,
table, caption, tbody, tfoot, thead, tr, th, td,
article, aside, canvas, details, embed,
figure, figcaption, footer, header, hgroup,
menu, nav, output, ruby, section, summary,
time, mark, audio, video {
	margin: 0;
	padding: 0;
	border: 0;
	font-size: 100%;
	font: inherit;
	vertical-align: baseline;
}
article, aside, details, figcaption, figure,
footer, header, hgroup, menu, nav, section {
	display: block;
}
body {
	line-height: 1;
}
ol, ul {
	list-style: none;
}
blockquote, q {
	quotes: none;
}
blockquote:before, blockquote:after,
q:before, q:after {
	content: '';
	content: none;
}
table {
	border-collapse: collapse;
	border-spacing: 0;
}
</style>
