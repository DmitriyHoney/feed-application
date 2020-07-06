<template>
    <div id="app">
        <div>
            <input id="colDesign" name="design" type="checkbox"   v-on:click="$emit('toggle-isColumn')"><label for="colDesign">Плитки</label>

        </div>

        <div>
            <h4>Кол-во отображаемых новостей</h4>
            <input id="number" type="number" value="10" max="15" min="1"
                   v-on:change="newsOnPage"
            />
        </div>

    </div>
</template>

<script>
    export default {
        components: {
            props: ['isColumn', 'changeNewsOnPage']
        },
        methods: {
            newsOnPage(e) {
                let num = e.target.value;
                this.$emit('changeNewsOnPage', num);
            }
        }
    }
</script>

<style>

</style>
