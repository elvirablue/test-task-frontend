<template>
    <div class="chip">
        <span v-text="item.name"/>
        <button
            @click="$emit('delete');"
        >
            X
        </button>
    </div>
</template>

<script>
    export default {
        name: "Chip",
        props: {
            item: {
                type: Object,
                required: true
            }
        },
    }
</script>

<style scoped lang="scss">
    .chip {
        display: inline-flex;
        justify-content: center;
        align-items: center;
        height: 30px;
        padding: 0 10px;
        background-color: lightblue;
        border-radius: 30px;

        button {
            flex-shrink: 0;
            display: inline-flex;
            align-items: center;
            justify-content: center;
            width: 20px;
            height: 20px;
            margin-left: 10px;
            font-size: 12px;
            line-height: 12px;
            color: white;
            background-color: rgba(0,0,0);
            border-radius: 50%;
        }
    }
</style>