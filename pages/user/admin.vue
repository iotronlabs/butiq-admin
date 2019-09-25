<template>
	<div>
		<div class="align">
			<v-chip small outline color="red">
				<v-avatar class="student-color"> A </v-avatar>
				Admin
				<v-spacer />
			</v-chip>
		</div>
		<br>
		<LoginForm id = "admin"/>
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
