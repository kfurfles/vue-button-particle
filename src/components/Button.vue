<template>
    <div class="button-container base-button">
        <button class="particles-button" @click="$emit('onClick')">Text Example</button>
    </div>
</template>

<script>
import '../plugins/particules'
import { onMounted } from '@vue/composition-api'

export default {
    data: () => ({
        button: null
    }),
    methods: {
        disintegrate() {
            this.button.disintegrate()
        },
        integrate(){
            this.button.integrate()
        }
    },
    mounted() {
        this.button = new Particles('.particles-button', 
            {
                type: 'rectangle',
                duration: 1000,
                easing: 'easeOutQuad',
                direction: 'top',
                size: 8
            }
        )
    }
}
</script>

<style lang="scss">
</style>