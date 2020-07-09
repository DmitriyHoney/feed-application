<template>
    <div>
        <input
                id="colDesign"
                name="design"
                type="checkbox"
                v-on:click="$emit('toggleIsColumn', getCheckboxState)"
        />
        <label for="colDesign">Плитки</label>
    </div>
</template>
<script>
    export default {
        components: {

        },
        methods: {
            getCheckboxState(e) {
                return e.target.value;
            }
        }

    }
</script>
<style></style>