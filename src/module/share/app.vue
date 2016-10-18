<template>

	<module-head title="程序大咖"></module-head>

	<model :model="model"></model>

	<!--banner-->
	<div class="banner">
		<ul>
			<li>
				<a href="#">
					<img src="http://wangda.oss-cn-hangzhou.aliyuncs.com/image/20151214111802283.jpg" />
				</a>
			</li>
		</ul>
	</div>
	<!--banner-->
	<!--message-->
	<div class="message" @click="getData">
		{{msg}}
	</div>
	<!--message-->
</template>

<script>
	import Lib from 'assets/Lib.js'

	import moduleHead from 'components/module-head'

	import model from 'components/model'

	/*import Button from 'components/Button';*/

	export default {
		data() {
				return {
					msg: 'hello share',
					model: {
						title: '标题',
						body: '<p>hello share</p>'
					}
				}
			},
			components: {
				moduleHead,
				model
			},
			ready() {

			},
			events: {
				'showModel': function() {
					this.$broadcast('showModel');
				}
			},
			methods: {
				getData: function() {
					this.$http.get("http://120.27.137.16/wangda/advert/queryAppAll.action?type=%E6%96%B0%E9%97%BB")
						.then(function(res) {
							console.log(res.data);
						}, function() {
							console.log("error")
						})
				}
			}
	}
</script>

<style scoped>
	.banner img {
		width: 100%;
		height: auto;
	}
	
	.message {
		height: 40px;
		line-height: 40px;
		border-left: 5px;
		padding-left: 10px;
	}
</style>