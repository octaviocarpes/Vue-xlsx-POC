<template>
    <div class="sheets-container">
        <div>
            <p>{{ sheet }}</p>
        </div>
    </div>
</template>
<script>
export default {
    name:'sheets-component',
    props: {
        sheet:Array
    },
}
</script>
<style lang="scss" scoped>

</style>
