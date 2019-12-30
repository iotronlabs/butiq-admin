<template>
	<div>

		<center>
		<v-chip class="ma-2" color="#673AB7"
	  text-color="#ffffff">
				
				Butiq Admin Login
				
			</v-chip>
		</center>
		<br>
		<LoginForm id = "store"/>
	</div>
</template>

<script>
import LoginForm from '@/components/LoginForm'

export default {
	layout: 'LoginLayout',
	components: {
		LoginForm
	}
}
</script>
<style scoped>
.align{
	text-align: center;
}

</style>

