<template lang="pug">
router-link(
	:to="{ name: 'EventDetails', params: { id: event.id }}"
	class="event-link"
)
	.event-card
		.event-image
			img(:src="event.image")
		span @{{ event.time }} on {{ event.date }}
		h4 {{ event.title }}
</template>

<script>
export default {
  name: 'EventCard',
  props: {
    event: {
			type: Object,
			required: true
		}
  }
}
</script>

<style scoped lang="scss">
.event-card {
	width: 15.625rem;
	margin-bottom: 1.125rem;
	padding: 1.25rem;
	border: 1px solid #39495c;
	transition: all 0.25s ease;
	cursor: pointer;
	&:hover {
		box-shadow: 0 0.1875rem 0.75rem 0 rgba(0,0,0,0.2);
		transform: scale(1.05);
	}
}
.event-link {
	color: #2c3e50;
	text-decoration: none;
}
.event-image {
	position: relative;
	margin-bottom: 1rem;
	&::after {
		content: '';
		display: block;
		padding-bottom: 100%;
	}
	img {
		position: absolute;
		top: 0;
		left: 0;
		right: 0;
		bottom: 0;
		width: 100%;
		height: 100%;
		object-fit: cover;
	}
}
</style>
