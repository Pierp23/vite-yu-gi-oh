<script>
import { store } from '../store';



export default {
    name: "MainComponent",
    data() {
        return {
            store
        }
    },
    methods: {

    }
}
</script>

<template>
    <main class="py-4">
        <div class="container px-0 my-3">
            <select>
                <option value="" selected>Select an archetype...</option>
                <option v-for="(archetype, i) in store.archetypes" :key="i" value="">
                    {{ archetype.archetype_name }}
                </option>
            </select>
        </div>
        <div class="container px-0 bg-white ">
            <div class="bg-black">
                <p class="text-white p-3">
                    Found {{ store.characters.length }} cards
                </p>
            </div>
            <div class="cards row d-flex px-5">
                <div class="col-4 col-md-3 col-lg-2" v-for="(character, i) in store.characters" :key="i">
                    <div class="single-card m-auto text-center my-3">
                        <div class="img-card ">
                            <img class="img-fluid" :src="character.card_images[0].image_url_small" alt="">
                        </div>
                        <div class="text-card">
                            <h4>
                                {{ character.name }}
                            </h4>
                            <h5>
                                {{ character.archetype }}
                            </h5>
                        </div>

                    </div>
                </div>

            </div>
        </div>
    </main>
</template>

<style lang="scss" scoped>
main {
    background-color: #D48F38;

    .single-card {
        max-width: 150px;
        background-color: #D48F38;
    }

    .img-card {
        max-width: 150px;
    }

}
</style>
