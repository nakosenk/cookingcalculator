<template>
    <div class="measurement">
        <div>Pounds: <input type="number" min="0" v-model.number="pounds"/> Oz: <input type="number" min="0" v-model.number="ounces"/></div>
        <div class="result">Result: {{result}}</div>
    </div>
</template>

<script lang="ts">
import { Component, Prop, Vue, PropSync } from 'vue-property-decorator';

@Component
export default class PoundsAndOunces extends Vue {
    @Prop() public rootMultiplier!: number;
    public data() {
        return {
            pounds: 1,
            ounces: 0,
        };
    }

    get result(): string {
        const raw: number = (this.$data.ounces + (this.$data.pounds * 16)) * this.rootMultiplier;
        const rawPounds: number = Math.floor(raw / 16);
        const rawOunces: number = raw % 16;

        return rawPounds + 'lbs ' + rawOunces + 'oz';
    }
}
</script>

<style scoped>
input {
    width: 50pt;
    border: 1pt solid #cecece;
    border-top: 0pt;
    border-left: 0pt;
    background-color: #eeeeee;
}

.measurement {
    border: 1pt;
    border-style:  solid;
    border-left: 0pt;
    border-top: 0pt;
    border-color: #cecece;
    background-color: #dedede;
    margin-top: 10pt;
    margin-bottom: 10pt;
}

.result {
    font-weight:  bold;
}
</style>