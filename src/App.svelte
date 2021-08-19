<script lang="ts">
	import DrumMachine from './lib/DrumMachine'
	import './app.scss'
</script>

<div class="wrapper">
	<DrumMachine length={16} />
</div>

<style lang="scss">
	:root {
		font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen,
			Ubuntu, Cantarell, 'Open Sans', 'Helvetica Neue', sans-serif;

		-webkit-touch-callout: none;
		-webkit-user-select: none;
		-khtml-user-select: none;
		-moz-user-select: none;
		-ms-user-select: none;
		user-select: none;
		-webkit-tap-highlight-color: transparent;
	}
	.wrapper {
		overflow: hidden;
		width: 100%;
		height: 100%;
	}
</style>
