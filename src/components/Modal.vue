<template>
<!-- @click.self är ett event modifier, den säger att vi enbart kör functionen när vi i detta fall klickar på backdrop. -->
    <div class="backdrop" @click.self="closeModal">
        <!-- Här så använder vi 'slot' som vi bögg i App.vue -->
        <div class="modal">
            <slot />
            <div class="actions">
                <slot name='links'></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: [
        
    ],
    methods: {
        closeModal() {
            this.$emit('close')
        }
    }
}
</script>

//Scoped betyder att dessa styles bara går på denna component
<style scoped>
    .modal {
        width: 400px;
        padding: 20px;
        margin: 100px auto;
        background-color: red;
        border-radius: 10px;
    }
    .backdrop{
        top: 0;
        position: fixed;
        background-color: rgba(0, 0, 0, 0.5);
        width: 100%;
        height: 100%;
    }
  

</style>