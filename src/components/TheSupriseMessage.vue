<template>
<div class="wrapper">
  <button 
    @click="thxAllert"
    class="glitch" 
    data-glitch="Keep smille!"
  >
    Keep smille!
  </button>
</div>
</template>

<script>
export default {
  name: 'TheSupriseMessage',
  methods: {
    thxAllert() {
      alert('Dziękuję za zadanie rekrutacyjne.');
    }
  }
}
</script>

<style scoped lang="scss">
.wrapper {
	width: 100%;
	height: 100%;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
}

.glitch {
	display: inline-block;
	cursor: pointer;
	background: transparent;
	border: none;
	width: fit-content;
	margin: 0 auto;
	font: {
		size: 54px;
		weight: 900;
	}
	text-decoration: none;
	position: absolute;
	top: 50%;
	left: 50%;
	transform: translate(-50%, -50%);
	margin: 0;
	color: #fff;
	letter-spacing: 5px;
	text-shadow: 0 2px 2px black;
	text-transform: uppercase;
	letter-spacing: -2px;
	
	&:before, &:after {
		display: block;
		text-transform: uppercase;
		content: attr(data-glitch);
		position: absolute;
		top: 0;
		left: 0;
		height: 100%;
		width: 100%;
		opacity: .8;
		animation-fill-mode: forwards;
	} &:after {
		color: #f0f;
		z-index: -2;
		animation: glitch .3s cubic-bezier(.25, .46, .45, .94) reverse both 5
	} &:before {
		color: #0ff;
		z-index: -1;
		animation: glitch .3s cubic-bezier(.25, .46, .45, .94) both 5
	}
}

@keyframes glitch {
	0% {
		transform: translate(0)
	}
	20% {
		transform: translate(-5px, 5px)
	}
	40% {
		transform: translate(-5px, -5px)
	}
	60% {
		transform: translate(5px, 5px)
	}
	80% {
		transform: translate(5px, -5px)
	}
	to {
		transform: translate(0)
	}
}

</style>
