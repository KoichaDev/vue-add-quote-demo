<template>
	<div>
		<p style="color: red">{{ quotes.length === 10 ? errorMessage : '' }}</p>

		<label class="progress__label" for="progress">{{ quotes.length }} / 10 </label>
		<progress id="progress" max="10" v-bind:value="quotes.length">
			{{ quotes.length }}
		</progress>
	</div>
</template>

<script>
export default {
	props: ['quotes', 'errorMessage'],
};
</script>

<style scoepd></style>
