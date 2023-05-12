<style scoped>
dl
{
	font-size: 180%;
}

</style>

<template>
<div class="fill scroll max-height">
	<div class="center-align middle-align" v-if="docContent == null">
		<div class="loader extra yellow"></div>
	</div>
	<div class="large-text left-align" v-else>
		<div class="markdown-body padding" v-html="docContent"></div>
	</div>
	<div v-for="i in 5" :key="i" class="large-space"></div>
</div>
</template>

<script setup>
import {onMounted, ref} from 'vue'
import {marked} from 'marked'
import DC from './FontPageDoc'

const docContent = ref(null)
onMounted(() => {
	docContent.value = marked.parse(DC)
})

</script>
