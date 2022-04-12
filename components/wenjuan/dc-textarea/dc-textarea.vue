<template>
	<view class="container-from">
		<view class="from-line"></view>
		<view class="from-content"><textarea adjust-position :placeholder="question.tip" v-model="question.value" type="text" /></view>
	</view>
</template>

<script>
export default {
	props: {
		question: {
			type: Object,
			default() {
				return {};
			}
		}
	},
	methods: {}
};
</script>

<style lang="scss">
@import url(@/static/scss/dcwj.scss);
/deep/ textarea {
	hidth: 100rpx !important;
	width: 100%;
}
</style>
