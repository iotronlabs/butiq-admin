<template>
    <div>
        <v-container fluid>
        <v-row align="center" justify="center">
            <v-col cols="4">
                <p class="display-1">Welcome to Admin Panel</p>
            </v-col>
        </v-row>
        <v-row>
            <v-col>
                <v-card
                    class="mx-auto text-center"
                    color="green"
                    dark
                    max-width="600"
                >
                    <v-card-text>
                    <v-sheet color="rgba(0, 0, 0, .12)">
                        <v-sparkline
                        :value="value"
                        color="rgba(255, 255, 255, .7)"
                        height="100"
                        padding="24"
                        stroke-linecap="round"
                        smooth
                        >
                        <template v-slot:label="item">
                            ${{ item.value }}
                        </template>
                        </v-sparkline>
                    </v-sheet>
                    </v-card-text>

                    <v-card-text>
                    <div class="display-1 font-weight-thin">Sales Last 24h</div>
                    </v-card-text>

                    <v-divider></v-divider>

                    <v-card-actions class="justify-center">
                    <v-btn block text>Go to Report</v-btn>
                    </v-card-actions>
                </v-card>
            </v-col>
            <v-col>
                <v-card height="370">
                    <v-card-title></v-card-title>
                </v-card>
            </v-col>
        </v-row>
        </v-container>
    </div>
</template>

<script>
  export default {
    data: () => ({
      value: [
        423,
        446,
        675,
        510,
        590,
        610,
        760,
      ],
    }),
  }
</script>