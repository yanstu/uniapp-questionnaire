<template>
	<view class="container shadow">
		<view class="container-title">
			<view v-if="question.must" class="title-bitian">*</view>
			<view class="title-xuhao">{{ indexTemp }}</view>
			<view class="title-text">{{ question.title }}:</view>
		</view>
		<component :question="question" :is="'dc-' + question.type"></component>
	</view>
</template>

<script>
import dcText from './dc-text/dc-text.vue';
import dcRadio from './dc-radio/dc-radio.vue';
import dcTextarea from './dc-textarea/dc-textarea.vue';
export default {
	data() {
		return { indexTemp: 0 };
	},
	props: {
		question: {
			type: Object,
			default() {
				return {};
			}
		},
		index: {
			type: Number(),
			default() {
				return 0;
			}
		}
	},
	mounted() {
		this.indexTemp = this.padNumber(this.index);
	},
	methods: {
		padNumber(num, fill = 2) {
			var len = ('' + num).length;
			return Array(fill > len ? fill - len + 1 || 0 : 0).join(0) + num;
		}
	},
	components: {
		dcText,
		dcRadio,
		dcTextarea
	}
};
</script>

<style lang="scss">
@import url(@/static/scss/dcwj.scss);
</style>
