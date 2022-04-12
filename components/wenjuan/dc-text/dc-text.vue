<template>
	<view class="container-from">
		<view class="from-line"></view>
		<view class="from-content"><input :placeholder="question.tip" v-model="question.value" type="text" /></view>
	</view>
</template>

<script>
export default {
	props: {
		question: {
			type: Object,
			default() {
				return { title: '预约接种人姓名', must: true, type: 'text', tip: '请输入姓名' };
			}
		}
	},
	methods: {}
};
</script>

<style lang="scss">
@import url(@/static/scss/dcwj.scss);
</style>
