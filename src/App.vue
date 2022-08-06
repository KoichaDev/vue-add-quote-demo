<template>
	<div class="container">
		<h1>Quote Added</h1>

		<label class="progress__label" for="progress">{{ quotes.length }} / 10 </label>
		<progress id="progress" max="10" v-bind:value="quotes.length">
			{{ quotes.length }}
		</progress>

		<form @submit.prevent="submit">
			<div class="form">
				<label for="quote">Quote</label>
				<textarea
					id="quote"
					cols="30"
					rows="10"
					v-bind:value="quoteText"
					@change="enteredQuote"
				></textarea>
			</div>
			<button type="submit">Add Quote</button>
		</form>
		<hr />
		<div>
			<p>JSON Stringify:</p>
			<pre>{{ JSON.stringify(quotes) }}</pre>
		</div>
		<p v-bind:key="index" v-for="(quote, index) in quotes" @click="deleteQuote(index)">
			{{ quote }}
		</p>
	</div>
</template>

<script>
export default {
	data() {
		return {
			quoteText: '',
			quotes: [],
		};
	},
	methods: {
		deleteQuote(indexPosition) {
			this.quotes.splice(indexPosition, 1);
		},
		enteredQuote(e) {
			const enteredText = e.target.value;
			this.quoteText = enteredText;
		},
		submit() {
			this.quotes.push(this.quoteText);
			this.quoteText = '';
		},
	},
};
</script>

<style scoped>
progress {
	width: 100%;
	height: 2em;
}
.form {
	display: flex;
	flex-direction: column;
}
</style>
