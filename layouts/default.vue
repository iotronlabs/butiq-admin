<template>
  <v-app dark>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      app
    >
		<v-list >

			<div>
				<v-layout row wrap>
					<v-flex xs10 sm10 md10 lg10>
						<UserProfile />
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
			<hr>
      		<v-list>
				<v-list-item
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
    </v-navigation-drawer>


	<v-app-bar
      :clipped-left="clipped"
      fixed
      app
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
	  <v-toolbar-title>Admin</v-toolbar-title>

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
        // {
        //   icon: 'mdi-apps',
        //   title: 'Welcome',
        //   to: '/'
        // },
        // {
        //   icon: 'mdi-chart-bubble',
        //   title: 'Inspire',
        //   to: '/inspire'
        // }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Vuetify.js'
    }
  }
}
</script>
