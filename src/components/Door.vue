<template>
    <div class="door-area">
        <div class="door-frame" :class="{ selected: selected && !open }">
            <Gift v-if="open && hasGift" />
        </div>
        <div 
            class="door" 
            :class="{ open }" 
            @click="selected = !selected"
        >
            <div class="number" :class="{ selected }">{{ number }}</div>
            <div 
                class="knob" 
                :class="{ selected }"
                @click.stop="open = true"
            ></div>
        </div>
    </div>
</template>

<script>
import Gift from './Gift'

export default {
    name: 'Door',
    components: { Gift },
    props: {
        number: {},
        hasGift: { type: Boolean }
    },
    data() {
        return {
            open: false,
            selected: false
        }
    }
}
</script>

<style>
:root {
    --door-border: 5px solid brown;
    --selected-border: 5px solid yellow;
}

.door-area {
    position: relative;
    width: 200px;
    height: 310px;
    margin-bottom: 20px;

    display: flex;
    justify-content: center;

    font-size: 3rem;
    border-bottom: 10px solid #AAA;
}

.door-frame {
    position: absolute;
    width: 180px;
    height: 300px;

    display: flex;
    justify-content: center;
    align-items: flex-end;

    border-left: var(--door-border);
    border-top: var(--door-border);
    border-right: var(--door-border);
}

.door {
    position: absolute;
    top: 5px;
    width: 170px;
    height: 295px;
    padding: 20px;

    display: flex;
    flex-direction: column;
    align-items: center;
    
    background: chocolate;
}

.door .knob {
    width: 20px;
    height: 20px;
    margin-top: 60px;
    
    align-self: flex-start;

    border-radius: 10px;
    background-color: brown;
}

.door-frame.selected {
    border-left: var(--selected-border);
    border-top: var(--selected-border);
    border-right: var(--selected-border);
}

.door > .number.selected {
    color: yellow;
}

.door > .knob.selected {
    background-color: yellow;
}

.door.open {
    background-color: #0007;
}

.door.open .knob {
    display: none;
}

.door.open {
    display: none;
}
</style>