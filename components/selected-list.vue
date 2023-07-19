<template>
    <ul class="selected-list">
        <li
                v-for="(item, index) in localValue"
                :key="`selected-item-${index}`"
                class="selected-list__item"
        >
            <chip
                    :item="item"
                    @delete="deleteItem(item)"
            />
        </li>
    </ul>
</template>

<script>
    export default {
        name: "SelectedList",
        props: {
            value: {
                type: Array,
                required: true
            }
        },
        computed: {
            localValue: {
                get() {
                    return this.value
                },
                set(value) {
                    this.$emit('input', value);
                }
            },
        },
        methods: {
            deleteItem(item) {
                this.localValue = this.localValue.filter(element => element.id !== item.id)
            }
        }
    }
</script>

<style scoped lang="scss">
    .selected-list {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;
        padding-top: 20px;
        margin: -4px 0;
        min-height: 96px;

        &__item {
            display: inline-flex;
            padding: 4px;
        }
    }
</style>