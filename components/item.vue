<template>
    <div :class="{
        'item': true,
        '-disabled': localValue
    }">
        <input
                type="checkbox"
                v-model="localValue"
                :name="`checkbox-${item.id}`"
                :id="`checkbox-${item.id}`"
        >
        <label
                :for="`checkbox-${item.id}`"
                v-text="item.name"
        />

    </div>
</template>

<script>
    export default {
        name: "Item",
        props: {
            item: {
                type: Object,
                required: true
            },
            value: Boolean
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
        }
    }
</script>

<style scoped lang="scss">
    .item {
        display: inline-flex;
        align-items: baseline;
        cursor: pointer;

        label {
            padding-left: 10px;
            cursor: inherit;
        }

        &.-disabled {
            pointer-events: none;
            cursor: default;

            label {
                opacity: 0.25;
            }
        }
    }
</style>