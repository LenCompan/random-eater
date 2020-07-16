<template>
	<div class="mx-auto mt-2">
		<b-card no-body class="overflow-hidden" style="max-width: 540px;">
			<b-row no-gutters>
			<b-col md="6">
				<b-card-img :src="place.img" alt="Image" class="rounded-0"></b-card-img>
			</b-col>
			<b-col md="6">
				<b-card-body v-bind:title="place.name">
				<b-card-text>
					{{ place.place }}<br>
					{{ place.description }}
				</b-card-text>
				</b-card-body>
			</b-col>
			</b-row>
		</b-card>
	</div>
</template>

<script>
export default {
	props: {
		place: {
			type: Object
		}
	}
}
</script>

<style>

</style>