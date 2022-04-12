<template>
	<view class="dcwj">
		<scroll-view class="scroll" :scroll-into-view="toIndex" scroll-with-animation show-scrollbar scroll-y>
			<image src="http://www.fgu.edu.tw/newpage/fguwebs/webs/clic/upload/images/Image/2020022417111858.jpg" style="height: 300rpx;width: 100vw;"></image>
			<view class="margin-top-sm" :id="'to' + (index + 1)" v-for="(question, index) in questionList"><wenjuan :index="index + 1" :question="question" /></view>
			<view class="bottom">
				<view class="status">
					一共
					<text class="text-blue">5</text>
					道题，已答
					<text class="text-green">2</text>
					道题，
					<text class="text-red">3</text>
					道题未答
				</view>
				<view @click="submit" class="submit-btn">提交</view>
			</view>
		</scroll-view>
	</view>
</template>

<script>
import wenjuan from '@/components/wenjuan/index.vue';
export default {
	data() {
		return {
			toIndex: '',
			questionList: [
				{
					title: '预约接种人姓名',
					must: true,
					type: 'text',
					tip: '请输入姓名',
					value: ''
				},
				{
					title: '您所住的楼栋',
					must: true,
					type: 'radio',
					value: '1',
					children: [
						{
							name: '半小时内',
							value: '1'
						},
						{
							name: '1小时内',
							value: '2'
						},
						{
							name: '2小时内',
							value: '3'
						},
						{
							name: '12小时内',
							value: '4'
						}
					]
				},
				{
					title: '您所住的楼栋',
					must: false,
					type: 'radio',
					value: '1',
					children: [
						{
							name: '半小时内',
							value: '1'
						},
						{
							name: '1小时内',
							value: '2'
						},
						{
							name: '2小时内',
							value: '3'
						},
						{
							name: '12小时内',
							value: '4'
						}
					]
				},
				{
					title: '您所住的楼栋',
					must: true,
					type: 'radio',
					value: '1',
					children: [
						{
							name: '半小时内',
							value: '1'
						},
						{
							name: '1小时内',
							value: '2'
						},
						{
							name: '2小时内',
							value: '3'
						},
						{
							name: '12小时内',
							value: '4'
						}
					]
				},
				{
					title: '您所住的楼栋',
					must: true,
					type: 'radio',
					value: '1',
					children: [
						{
							name: '半小时内',
							value: '1'
						},
						{
							name: '1小时内',
							value: '2'
						},
						{
							name: '2小时内',
							value: '3'
						},
						{
							name: '12小时内',
							value: '4'
						}
					]
				}
			]
		};
	},
	components: {
		wenjuan
	},
	onLoad() {},
	methods: {
		submit() {
			console.log(this.questionList);
			for (let index in this.questionList) {
				var question = this.questionList[index];
				if (!question.value && question.must) {
					uni.showToast({
						title: '请先完成表单',
						icon: 'none'
					});
					this.jump(parseInt(index) + 1);
					return;
				}
			}
			uni.showToast({
				title: '提交成功',
				icon: 'success'
			});
		},
		jump(index) {
			this.toIndex = 'to' + index;
			console.log(this.toIndex);
			setTimeout(() => {
				this.toIndex = '';
			}, 10);
		}
	}
};
</script>

<style lang="scss">
.dcwj {
	height: 100vh;
}
.submit-btn {
	margin-top: 20rpx;
	width: 100%;
	height: 90rpx;
	display: flex;
	justify-content: center;
	align-items: center;
	background-color: #0081ff;
	border-radius: 10rpx;
	color: white;
}
.bottom {
	margin-top: 100rpx;
	margin-left: 2.5%;
	width: 95%;
	padding-bottom: 100rpx;
}
.scroll {
	width: 100%;
	height: 100%;
}
.status {
	text-align: right;
	font-size: 30rpx;
	text {
		margin: 0 5rpx;
	}
}
</style>
