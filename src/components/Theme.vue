<template>
    <div class="theme">
        <div class="theme__box">
            <label class="theme__label" for="theme">
                <input class="theme__toggle" id="theme" type="checkbox">
            </label>
        </div>
    </div>
</template>
<script>
export default {
    name: 'Theme'
}
</script>
<style lang="scss">
.theme{
    position: absolute;
    top: 5%;
    right: 15%;
    width: 60px;
    height: 30px;
    border: 1px solid green;
    &__label{
        border: 1px solid red;
        position: absolute;
        top: 0;
        left: 0;
        right: 0;
        bottom: 0;
        cursor: pointer;
    }
}
</style>