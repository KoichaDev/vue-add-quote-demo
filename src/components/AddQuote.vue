<template>
	<form @submit.prevent="submit">
		<div class="form">
			<label for="quote">Quote</label>
			<textarea id="quote" cols="30" rows="10" v-model="quoteText"></textarea>
		</div>
		<button type="submit">Add Quote</button>
	</form>
</template>

<script>
export default {
	data() {
		return {
			quoteText: '',
		};
	},
	methods: {
		submit(e) {
			this.$emit('add-quote', this.quoteText);
			this.quoteText = '';
		},
	},
};
</script>

<style scoped>
.form {
	display: flex;
	flex-direction: column;
}
</style>
