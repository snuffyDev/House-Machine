<script lang="ts">
	export let type = 'kick'
	export let active = false
</script>

<div class="pad" on:click={() => (active = !active)} class:active />

<style lang="scss">
	.pad {
		width: 3rem;
		height: 3rem;
		background: #303948;
		&.active {
			background: #7d93ba;
		}
	}
</style>
