<template>
	<div class="flex justify-center min-h-screen min-w-full bg-emerald-600">
		<div class="bg-black min-w-[30%] min-h-screen border-x-8 border-white border-dashed" id="gameArea">
			<div class="min-h-[15%] max-w-[13%] rounded-[30%] bg-red-600"
				:style="{ top: car.y + '%', left: car.x + '%' }"></div>
			<button class="bg-emerald-600 rounded-[10%]" @click="handleStart">Start</button>
		</div>
	</div>
</template>
<script setup>
import { ref } from 'vue'
const keyControl = ref(null)
const car = ref({ x: 85, y: 85 })
const enemyCar=`<div class="min-h-[15%] max-w-[13%] rounded-[30%] bg-red-600" :style="{ top: '50%', left: '50%' }"></div>`
function handleStart(e) {
	keyControl.value = () => {
		e.target.style.display='none'
		document.addEventListener('keydown', (event) => {
			if (car.value.y < 84 && event.key == 'ArrowDown') car.value.y += 2
			else if (car.value.y > 10 && event.key == 'ArrowUp') car.value.y -= 2
			else if (car.value.x > 1 && event.key == 'ArrowLeft') car.value.x -= 2
			else if (car.value.x < 86 && event.key == 'ArrowRight') car.value.x += 2
		})
	}
	setInterval(()=>{
		document.getElementById('gameArea').innerHtml+=enemyCar
		console.log(document.getElementById('gameArea'))
	},2000)
	keyControl.value()
}
</script>