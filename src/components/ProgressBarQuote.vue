<template>
	<div>
		<p style="color: red">{{ errorMessage }}</p>

		<label class="progress__label" for="progress">{{ quotes.length }} / {{ maxQuotes }} </label>
		<progress id="progress" max="10" v-bind:value="quotes.length">
			{{ quotes.length }}
		</progress>
	</div>
</template>

<script>
export default {
	props: ['quotes', 'maxQuotes', 'errorMessage'],
};
</script>

<style scoepd></style>
