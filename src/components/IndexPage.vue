<style scoped>
i, div, h5, a, span {
	text-shadow: 1px 1px 3px lightsalmon, 1px 1px 1px grey;
}
</style>

<template>
<div class="fill middle-align center-align max-height scroll">
	<div class="center-align large-text">
		<i class="extra">donut_small</i>
		<h5 class="center-align light-blue-text">一个小小的 CDN 型项目</h5>
		<p class="italic small-text cyan-text">
			<a href="https://zh.wikipedia.org/zh-cn/%E7%A0%B9" target="_blank" class="indigo-text">
				砹 Astatine, <span class="tooltip">来点 Wiki?</span>
			</a>
			<span class="brown-text">
				At,
				Assets Table
			</span>
		</p>
		<p class="">开发过程有些资源找不到合适的 CDN</p>
		<p>(主要是各类字体)</p>
		<p class="">于是在 GitHub Pages 和 Cloudflare Pages</p>
		<p class="">建立本项目用于加速资源访问</p>
		<p class="purple-text">如本站访问速度不佳, 请点击右上角按钮切换访问源</p>
		<p class="purple-text">(其中自定义域名源一般不需要挂梯子)</p>
		<p class="green-text">本站提供所有资源<span class="deep-orange-text">仅</span>可用于个人非商用用途</p>
		<div class="space"></div>
		<nav class="center-align">
			<a href="https://github.com/FirokOtaku/astatine-gear" target="_blank">
				<button class="tertiary round elevate">
					<i class="medium-text">code</i>
					GitHub

					<div class="tooltip space">
						虽然没什么太有用的东西 <br>
						想看看源码吗? <br>
					</div>
				</button>
			</a>

			<button class="primary round elevate" @click="$emit('sp', 'font')">
				<i class="medium-text">text_fields</i>
				字体资源

				<div class="tooltip space">
					康康有什么好料!
				</div>
			</button>
		</nav>

		<div class="large-space"></div>
		<table>
			<tbody>
			<tr v-for="changelog in listChangelog" :key="changelog.date">
				<td>{{ changelog.date }}</td>
				<td>{{ changelog.title }}</td>
				<td v-html="changelog.desc"></td>
			</tr>
			</tbody>
		</table>
	</div>
</div>
</template>

<script setup>
import {computed} from "vue";

defineEmits(['sp'])
const listChangelog = computed(() => {
	return [
		{ date: '2023-05-14', title: '增加字体资源', desc: `汉仪文黑<br>Cabin` },
		{ date: '2023-05-12', title: '增加字体资源', desc: `Source Code Pro` },
	]
})
</script>
