<script lang="ts">
	import type { InputRule } from '$types/autocomplete';
	import { CONSTANTS } from '$stores/constants';
	import { Col, TextField } from 'svelte-materialify';
	import { createEventDispatcher } from 'svelte';

	export let cols: number | undefined = undefined;
	export let sm: number | undefined = undefined;
	export let md: number | undefined = undefined;
	export let lg: number | undefined = undefined;
	export let xl: number | undefined = undefined;
	export let value = '';
	export let min: string | undefined = undefined;
	export let max: string | undefined = undefined;
	export let rules: InputRule[] = [];

	$: constants = $CONSTANTS;
	let dispatcher = createEventDispatcher();
</script>

<Col {cols} {sm} {md} {lg} {xl}>
	<TextField
		color={constants.AMADEUS_BLUE}
		type="date"
		{min}
		{max}
		{rules}
		bind:value
		on:change={() => dispatcher('change')}
	>
		<slot />
	</TextField>
</Col>
