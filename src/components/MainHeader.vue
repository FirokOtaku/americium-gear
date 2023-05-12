<style scoped>

</style>

<template>
<header class="secondary" style="z-index: 1">
	<nav>
		<button class="circle transparent" @click="$emit('sp', 'index')">
			<i>donut_small</i>
		</button>
		<h5 class="max left-align">砹齿轮</h5>

		<button class="circle transparent">
			<i class="extra">
				<img src="../assets/CF_logomark_singlecolor_blk.svg" alt="cloudflare-logo"
				     v-if="cw === 'cloudflare-pages' || cw === 'cloudflare-pages-custom-domain'">
				<img src="../assets/github-mark.svg" alt="github-logo"
				     v-else-if="cw === 'github-pages'">
				<template v-else-if="cw === 'localhost'">api</template>
				<template v-else>help</template>
			</i>
			<div class="tooltip space left">
				当前访问基于<br>{{
					cw === 'cloudflare-pages' ? 'Cloudflare Pages' :
						cw === 'localhost' ? '本地开发服务器' :
							cw === 'github-pages' ? 'GitHub Pages' :
								cw === 'cloudflare-pages-custom-domain' ? 'Cloudflare Pages (自定义域名)' :
									'未知'
				}}
			</div>

			<div class="dropdown no-wrap left">
				<a v-if="cw !== 'github-pages'" href="https://firokotaku.github.io/astatine-gear/">
					<i class="small">arrow_circle_right</i>
					切换至 GitHub Pages 访问
				</a>
				<a v-if="cw !== 'cloudflare-pages'" href="https://astatine-gear.pages.dev/astatine-gear/">
					<i class="small">arrow_circle_right</i>
					切换至 Cloudflare Pages 访问
				</a>
				<a v-if="cw !== 'cloudflare-pages-custom-domain'" href="http://astatine-gear.firok.space/astatine-gear/">
					<i class="small">arrow_circle_right</i>
					切换至 Cloudflare Pages (自定义域名) 访问
				</a>
			</div>
		</button>
	</nav>
</header>
</template>

<script setup>
import {computed} from "vue";

defineEmits(['sp'])

const cw = computed(() => {
	if(Origin.indexOf('localhost') >= 0 || Origin.indexOf('127.0') >= 0 || Origin.indexOf('192.168') >= 0)
	{
		return 'localhost'
	}
	else if(Origin.indexOf('worker.dev') >= 0 || Origin.indexOf('pages.dev') >= 0) // https://astatine-gear.firok.workers.dev/
	{
		return 'cloudflare-pages'
	}
	else if(Origin.indexOf('firok.space') >= 0) // http://astatine-gear.firok.space/
	{
		return 'cloudflare-pages-custom-domain'
	}
	else if(Origin.indexOf('github.io'))
	{
		return 'github-pages'
	}
	else return 'unknown'
})


</script>
