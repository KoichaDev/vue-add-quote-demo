<template>
	<div class="container">
		<h1>Quote Added</h1>

		<progress-bar :quotes="quotes" :maxQuotes="maxQuotes" :errorMessage="errorMessage" />

		<add-quote @add-quote="addQuote" />
		<hr />

		<view-quotes :quotes="quotes" @delete-quote="deleteQuote" />
	</div>
</template>

<script>
import ProgressBarQuote from './components/ProgressBarQuote.vue';
import AddQuote from './components/AddQuote.vue';
import ViewQuotes from './components/ViewQuotes.vue';

export default {
	data() {
		return {
			errorMessage: '',
			quotes: [],
			maxQuotes: 10,
		};
	},
	components: {
		'progress-bar': ProgressBarQuote,
		'add-quote': AddQuote,
		'view-quotes': ViewQuotes,
	},
	methods: {
		deleteQuote(index) {
			console.log(index);
			this.quotes.splice(index, 1);
			this.errorMessage = '';
		},
		addQuote(value) {
			if (value === '') {
				return (this.errorMessage = 'Please enter a quote');
			}

			if (this.quotes.length === this.maxQuotes) {
				return (this.errorMessage =
					'You have reached the maximum number of quotes! Please delete one before adding another.');
			}

			this.quotes.push(value);
		},
	},
};
</script>

<style scoped>
progress {
	width: 100%;
	height: 2em;
}
</style>
