<template>
  <v-app dark>
    
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
		<v-list shaped>

			<div>
				<v-layout row wrap>
					<v-flex xs10 sm10 md10 lg10>
						<v-subheader>&emsp;
            <v-avatar color = "indigo" size= "48"></v-avatar>&emsp;
             Name</v-subheader>
					</v-flex>
          
					<v-flex xs2 sm2 lg2 md2>
						<v-list>
							<v-list-tile-action>
								<v-btn icon
									@click.stop="closeDrawerModel">
								<!-- <font-awesome-icon :icon="['fas', 'times']"/> -->

								</v-btn>

							</v-list-tile-action>
						</v-list>
					</v-flex>
				</v-layout>
			</div>
      <br>
			<hr>
      <v-list>
				<v-list-item color="primary"
					v-for="(item, i) in items"
					:key="i"
					:to="item.to"
					router
					exact
				>
					<v-list-item-action>
						<v-icon>{{ item.icon }}</v-icon>
					</v-list-item-action>
					<v-list-item-content>
						<v-list-item-title v-text="item.title" />
					</v-list-item-content>
				</v-list-item>
    	</v-list>
		</v-list>
    <br><br><br><br><br><br><br><br><br><br>
    <v-btn block outlined class="white--text" color="primary"><v-icon>mdi-logout</v-icon> Logout</v-btn>
    
    </v-navigation-drawer>


	<v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
    
    <v-row align="center">
      <v-col cols="2">
        <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      </v-col>
      <v-col cols="2" offset="3" >
        <v-toolbar-title><nuxt-link to="/dashboard"><v-img height="8vh" contain src="/butiq.png"/></nuxt-link></v-toolbar-title>
      </v-col>
      <v-col cols="1" offset="3">
        <v-icon>mdi-account-circle</v-icon>
      </v-col>
      <v-col cols="1" >
        <v-icon>notifications</v-icon>
      </v-col>
    </v-row>
    </v-app-bar>


	<v-content>
      <v-container>
        <nuxt />
      </v-container>
    </v-content>


	<v-footer
      :fixed="fixed"
      app
    >
      <span>&copy; 2019</span>
    </v-footer>
  </v-app>
</template>

<script>
import Userprofile from '@/components/UserProfile'
export default {
	components: {
		Userprofile
	},
  data () {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Dashboard',
          to: '/dashboard'
        },
        

            {
              icon:'settings',
              title : 'Configure',
              to : '/configure/users'
              
            },
            {
              icon:'mdi-format-list-checkbox',
              title : 'Category',
              to : '/category-table'
            },
            {
              icon:'mdi-tshirt-crew',
              title : 'Products',
              to : '/add-product'
            },
            {
              icon:'people',
              title : 'Users',
              to : '/'
            },
            {
              icon:'mdi-cart',
              title : 'Add Store',
              to : '/'
            }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>