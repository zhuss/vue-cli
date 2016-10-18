<template>
	<div class="mark" v-show="isShow" transition="fead" @click="close">
		<div class="model">
			<h1 class="model_title">{{model.title}}</h1>
			<div class="model_body">
				{{{model.body}}}
			</div>
			<div class="model_bottom">
				<button @click="close">取消</button>
				<button @click="close" class="confirm">确定</button>
			</div>

		</div>

	</div>
</template>

<script>
	import Lib from 'assets/Lib.js'

	module.exports = {
		components: {

		},
		data: function() {
			return {
				msg: 'Hello moto! what`s up,yaoyao',
				isShow: false
			}
		},
		ready() {

		},
		watch: {
			'isShow': function(val) {
				if(val) {
					document.addEventListener("touchmove", this.prevent, false);
				} else {
					document.removeEventListener("touchmove", this.prevent, false);
				}
			}
		},
		methods: {
			prevent: function(e) {
				e.preventDefault();
			},
			close: function() {
				this.isShow = false;
			}
		},
		props: {
			"model": {
				type: Object,
				default: {
					title: 'title',
					body: '<p>message</p>'
				}
			}
		},
		events: {
			'showModel': function() {
				this.isShow = true;
			}
		}
	}
</script>

<style scoped>
	.mark {
		position: fixed;
		top: 0;
		left: 0;
		width: 100%;
		height: 100%;
		background: rgba(0, 0, 0, .5);
	}
	
	.show {
		display: block;
	}
	
	.hide {
		display: none;
	}
	/* 必需 */
	
	.fead-transition {
		transition: all .3s ease;
		opacity: 1;
		transform: scale(1);
	}
	/* .expand-enter 定义进入的开始状态 */
	/* .expand-leave 定义离开的结束状态 */
	
	.fead-enter {
		transform: scale(1.1);
		opacity: 0;
	}
	
	.fead-leave {
		transform: scale(1.1);
		opacity: 0;
	}
	
	.model {
		position: absolute;
		left: 50%;
		top: 50%;
		transform: translate(-50%, -50%);
		width: 60%;
		padding: 20px;
		background: #FFF;
	}
	
	.model_title {
		font-size: 16px;
		font-weight: normal;
	}
	
	.model_body {
		padding: 20px 0;
	}
	
	.model_bottom {
		width: 100%;
		display: flex;
	}
	
	.model_bottom button {
		flex: 1;
		border: none;
		background: #FFF;
		font-size: 14px;
		font-weight: 100;
	}
	
	.model_bottom .confirm {
		color: #04BE02;
	}
</style>