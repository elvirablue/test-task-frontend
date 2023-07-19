<template>
    <div class="app">
        <h1> test-task-frontend</h1>

        <div class="container">
            <div class="card">
                <h3>Выбранные вещи из вещей пользователя</h3>
                <selected-list v-model="selectedUserList"/>
            </div>
            <div class="card">
                <h3>Выбранная вещь из вещей на выбор</h3>
                <selected-list v-model="selectedAllList"/>
            </div>

            <div class="card">
                <h3>Вещи у пользователя</h3>
                <div v-if="maxUserList > selectedUserList?.length">Вы можете выбрать до 6 вещей</div>
                <div v-else class="color-red">Вы выбрали максимальное количество вещей</div>
                <main-list
                        v-if="userList.length"
                        v-model="selectedUserList"
                        :list="userList"
                        :disabled="maxUserList === selectedUserList?.length"
                />
            </div>
            <div class="card">
                <h3>Вещи на выбор</h3>
                <div>Вы можете выбрать только 1 вещь</div>
                <main-list
                        v-if="allList.length"
                        v-model="selectedAllList"
                        :list="allList"
                        :disabled="maxAllList === selectedAllList.length"
                />
            </div>
        </div>
    </div>
</template>

<script>
    import USER_LIST from '~/core/user-items-data.json';
    import ALL_LIST from '~/core/all-items-data.json';
    export default {
        name: 'IndexPage',
        data: () => ({
            userList: USER_LIST,
            allList: ALL_LIST,
            selectedUserList: [],
            selectedAllList: [],
            maxUserList: 6,
            maxAllList: 1,
        })
    }
</script>

<style lang="scss" scoped>
    h1 {
        display: block;
        padding-bottom: 40px;
        text-align: center;
    }
</style>
