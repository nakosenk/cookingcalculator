<template>
    <div>
        <div>Pounds: <input type="number" min="0" v-model.number="pounds"/></div>
        <div>Oz: <input type="number" min="0" v-model.number="ounces"/></div>
        <div>Multiplier: <input type="number" min="0" v-model.number="multiplier"/></div>
        <div>Result: {{result}}</div>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, PropSync } from 'vue-property-decorator';

@Component
export default class PoundsAndOunces extends Vue {
    public data() {
        return {
            pounds: 1,
            ounces: 0,
            multiplier: 2,
        };
    }

    get result(): string {
        const raw: number = (this.$data.ounces + (this.$data.pounds * 16)) * this.$data.multiplier;
        const rawPounds: number = Math.floor(raw / 16);
        const rawOunces: number = raw % 16;

        return rawPounds + 'lbs ' + rawOunces + 'oz';
    }
}
</script>

<style scoped>

</style>