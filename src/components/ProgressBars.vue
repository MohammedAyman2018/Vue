<template>
	<div>

        <div v-if="missions.length > 0" class="prop" style="margin-top: 60px">
            <div class="progress">
                <div class="determinate" :style="{ width: missions.length * 10 + '%' }"> </div>
            </div>
            <p>{{ missions.length * 10  }}%</p>
        </div>

        
	</div>
</template>

<script>

export default {
	name: 'progress',
    props:{
        missions: Array
    }
}
</script>

<style scoped>

</style>

