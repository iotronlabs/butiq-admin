<template>
<div>
    <v-form @submit.prevent="checklogin" id = "login-form" class = "login-form" method = "post"> 
        <v-text-field 
        prepend-icon = "person"
        label = "Email ID"
        placeholder = " "
        name = "emailid"
        type = "emailid"
        v-model ="email"
        :rules ="[rules.required,rules.emailValid]"
        autocomplete = "off"
        required>
        </v-text-field>
        <v-text-field
        id="password"
        prepend-icon="lock"
        v-model="password"
        :append-icon="show ? 'visibility' : 'visibility_off'"
        :rules="[rules.required, rules.min]"
        :type="show ? 'text' : 'password'"
        name="password"
        label="Password"
        placeholder=" "
        hint="At least 8 characters"
        counter
        autocomplete="off"
        @click:append="show = !show">
        
        </v-text-field>
        &nbsp;&nbsp;<a href="#">forgot password?</a>
		<v-checkbox
			v-model="checkbox"
			label="Remember Me"
		></v-checkbox>

        <v-btn
        :disabled="disabled"
        block
        color="primary"
        type="submit"
        form="login-form"
        :class="disabled ? 'btn-login' : 'btn-login-color'">
                LogIn
        </v-btn>

    </v-form>

    <!-- snackbar -->
	<v-snackbar
		v-model="snackbar"
		:timeout="timeout"
		top
		vertical
    >
		{{ message }}
		<v-btn
			color="pink"
			flat
			@click="snackbar = false"
		>
			Close
		</v-btn>
    </v-snackbar>
</div>
</template>

<script>
export default {
    name: 'LogInForm',
	props : {
		id: String
	},
	data() {
		return {
			email: '',
			password: '',
			authentication: '',
			show: false,
			rules: {
				required: v => !!v || 'Required.',
				min: v => v.length >= 8 || 'Min 8 characters',
				emailValid : v=> /.+@.+/.test(v) || 'E-mail must be valid'
			},
			checkbox: false,
			button: 'btn-login',
			snackbar: false,
			timeout: 3000,
			message: '',
			url : ''
		}
    },
    
    computed: {
		disabled() {
			if(this.email.length==0 || this.password.length<8 || this.email==/.+@.+/.test(this.email))
			{
				return true
			}
			else
			{
				return false
			}
		}
    },
    
    
    
}
</script>

<style lang="css" scoped>
.login-form {
	padding-left: 20px;
	padding-right: 20px;
}
.btn-login-color {
	border-radius: 10px;
	background-image: linear-gradient(to top,#4e54c8 0%, #8f94fb 100%);
	color: aliceblue;
}
.btn-login {
	border-radius: 10px;
}
</style>



