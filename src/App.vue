
<style scoped>
.content-body
{
	height: calc(100vh - 64px);
}
.slide-fade-enter-active { transition: opacity 0.8s ease-in; }
.slide-fade-leave-active { transition: opacity 0.6s ease-in; }
.slide-fade-enter-from, .slide-fade-leave-to { opacity: 0; }
</style>

<template>
	<main-header @sp="cp = $event"/>

	<div class="content-body">
		<transition name="slide-fade">
			<component :is="cpi" @sp="cp = $event" />

		</transition>
	</div>
</template>

<script setup>
import {computed, ref} from 'vue'
import FontPage from './components/FontPage.vue'
import EmptyPage from './components/EmptyPage.vue'
import IndexPage from './components/IndexPage.vue'
import MainHeader from "./components/MainHeader.vue";

// index, index-font
const cp = ref('index')
const cpi = computed(() => {
	switch (cp.value)
	{
		case 'index': return IndexPage
		case 'font': return FontPage
		default: return EmptyPage
	}
})

</script>
