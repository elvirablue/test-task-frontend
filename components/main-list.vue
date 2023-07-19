<template>
    <ul :class="{
        'main-list': true,
        '-disabled': disabled
    }">
        <li
                v-for="(item, index) in list"
                :key="`users-item-${index}`"
                class="main-list__item"
        >
            <item
                    :item="item"
                    :value="!!(localValue?.length && localValue.find(element => element.id === item.id))"
                    @input="selectItem(item)"
            />
        </li>
    </ul>
</template>

<script>
    export default {
        name: "MainList",
        props: {
            list: {
                type: Array,
                required: true
            },
            value: {
                type: Array,
                default: null,
            },
            disabled: Boolean,
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
            selectItem(item) {
                this.localValue.push(item)
            }
        }
    }
</script>

<style scoped lang="scss">
    .main-list {
        display: block;
        padding-top: 40px;

        &.-disabled {
            pointer-events: none;
        }

        &__item {
            display: block;
            padding: 10px 0;
        }
    }
</style>