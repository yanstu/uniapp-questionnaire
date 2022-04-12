<template>
	<view class="container-from">
		<view class="from-line"></view>
		<view class="from-content">
			<radio-group class="from-radio-group" v-model="question.value" @change="change">
				<view v-for="(item, index) in question.children">
					<label class="from-radio">
						<radio class="blue" :class="question.value == item.value ? 'checked' : ''" :checked="question.value == item.value" :value="item.value"></radio>
						<view class="title">{{ item.name }}</view>
					</label>
					<view class="from-line" v-if="index != question.children.length - 1"></view>
				</view>
			</radio-group>
		</view>
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
	methods: {
		change(e) {
			this.question.value = e.detail.value;
		}
	}
};
</script>

<style lang="scss">
@import url(@/static/scss/dcwj.scss);
.from-radio-group {
	display: flex;
	flex-direction: column;
}
.from-radio {
	display: flex;
	align-items: center;
	radio {
		margin-right: 20rpx;
	}
}
</style>
