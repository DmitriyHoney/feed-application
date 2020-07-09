<template>
    <div>
        <h4>
            Кол-во отображаемых новостей
        </h4>
        <input
                id="number"
                type="number"
                max="15"
                min="1"
                v-bind:value="checkboxValue"
                v-on:change="changeCheckboxValue"
        />
    </div>
</template>

<script>
    export default {
        props: ['newsOnPage'],
        data() {
            return {
                checkboxValue: this.newsOnPage,
            }
        },
        methods: {
            changeCheckboxValue(e) {
                this.checkboxValue = e.target.value;
                this.$emit('changeNewsOnPage', this.checkboxValue)
            }
        }
    }
</script>

<style></style>