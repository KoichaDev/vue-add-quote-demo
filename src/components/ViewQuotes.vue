<template>
	<div>
		<p>JSON Stringify:</p>
		<pre>{{ JSON.stringify(quotes) }}</pre>

		<p v-bind:key="index" v-for="(quote, index) in quotes" @click="deleteQuote(index)">
			{{ quote }}
		</p>
	</div>
</template>

<script>
export default {
	props: {
		quotes: {
			type: Array,
		},
	},
	methods: {
		deleteQuote(index) {
			this.$emit('delete-quote', index);
		},
	},
};
</script>

<style></style>
