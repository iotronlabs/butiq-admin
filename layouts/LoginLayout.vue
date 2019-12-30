<template>
<div >
	
	<particles-bg type="cobweb" color="#5E35B1" :bg="true" /> 
	
	
    <v-container fluid class="hidden">
		<v-row class="mt-12" align="center" justify="center">
			<v-col  cols="8" offset="2" md="4" offset-md="2" >
				<br><br><br><br><br><br><br><br>
				<v-img src="/butiq.png"></v-img>
			</v-col>
			<v-col cols="1"></v-col>
			<v-col cols="12" md="4">
				<br><br><br><br><br><br>
				<v-card  class = "elevation-1 card-design">            
					<v-card-text>
						<nuxt />
					</v-card-text>
				</v-card>
			</v-col>
		</v-row>
    </v-container>					
	        
    

    <v-footer app class="footer" >
		<v-layout>
			<v-flex>
				Made with <span class="heart">&hearts;</span> by
				<a href="http://www.iotronlabs.com" target="_blank" class="footer-link">Iotronlabs</a>
			</v-flex>
		</v-layout>
    </v-footer>
	


	   


</div>
</template>
    


<script>
export default {
	
	name: 'LoginLayout',
	
}
</script>

<style scoped>

.container-grad
{
	background-image: linear-gradient(to top,#4e54c8 0%, #8f94fb 100%);	
}
.login-grad
{
	background-image: linear-gradient(to right,#434343 0%, black 100%);
	border-radius: 0px 0px 15px 15px;
}

.v-toolbar {
	height: 60px;
}

.card-design {
	border-radius: 10px;
	
}
.toolbar-text {
	font-size: 1.5em;
	color: white;
}
img
{
	height: 30px;
	width: 25%;
	min-width: 100px;
}
.footer
{
	background-image: linear-gradient(to top,#673AB7 0%, #a283f0 100%);
	text-align: center;
	color: white;
	
}
.heart
{
	color: #e25555;
}
.footer-link
{
	text-decoration: none;
	color: #fff;
}

</style>
