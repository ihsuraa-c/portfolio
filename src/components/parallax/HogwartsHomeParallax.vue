<script setup>
import {useHomeStore} from "@/stores/store-home";
import ExploreProjectButton from "../buttons/ExploreProjectButton.vue";
import {useUiStore} from "@/stores/store-ui";
import FloatingLights from "../effects/FloatingLights.vue";

const home = useHomeStore();
const ui = useUiStore();
</script>

<template>
    <v-parallax
        :src="home.header.parallax.location"
        :height="$vuetify.display.smAndUp && $vuetify.display.smAndDown ? 500 :
        $vuetify.display.mdAndUp && $vuetify.display.mdAndDown ? 550 :
        $vuetify.display.lgAndUp && $vuetify.display.lgAndDown ? 600 : 620"
    >
        <FloatingLights :count="20" :attraction-force="0.2" :responsive="true">
            <v-container class="d-flex flex-column fill-height justify-center align-center text-white">
                <h1 class="text-h3 text-sm-h2 mb-4 text-md-h1 text-shadow potter text-center">
                    {{ home.header.title }}
                </h1>
                <p class="text-shadow text-subtitle-2 text-sm-subtitle-1 text-md-h5 my-3 my-sm-0 text-center"
                   :class="{
                        'text-grey-lighten-3': ui.getTheme === 'dark',
                        'text-grey-lighten-2': ui.getTheme === 'light'
                   }"
                >
                    {{ home.header.subtitle }}
                </p>
                <explore-project-button/>
            </v-container>
        </FloatingLights>
    </v-parallax>
</template>

<style scoped>

</style>