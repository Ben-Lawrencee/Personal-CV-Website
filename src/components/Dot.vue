<template>
    <div class="dot"/>
</template>

<script>
export default {
    name: "Dot"
}
</script>

<style lang="scss">

@import '@/GlobalVariables.scss';


.dot {
    position: relative;
    width: 8px;
    height: 8px;
    border-radius: 50%;
    background-color: $primary;
    margin-inline: 5px;

    --dash-width: 8px;

    &::before {
        content: '';
        
        width: var(--dash-width);
        height: 2px;
        
        position: absolute;
        translate: 100%;
        top: calc(50% - 1px);
        left: -200%;
        
        background: linear-gradient(to left, $primary, transparent);
    }

    &::after {
        content: '';
        
        width: var(--dash-width);
        height: 2px;
        
        position: absolute;
        translate: 0%;
        top: calc(50% - 1px);
        left: 100%;
        
        background: linear-gradient(to right, $primary, transparent);
    }
}

</style>