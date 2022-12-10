<script setup>

import Minicard from './Minicard.vue'
</script>

<template>
    <div class="main_module_sidebar">
        <div class="main_module_sidebar_serch">
            <span>Поиск сотрудников</span>
            <input type="text" v-model="inputValue" placeholder="Введите Id или имя " @input="inputAction">
        </div>
        <div class="main_module_sidebar_results">
            <span>Результаты </span>
            <div class="message" v-if="findedUsers.length === 0">{{ message }}</div>
            <Minicard v-else v-for="item in findedUsers" :key="item.username" @click="select" :id="item.username"
                :item="item" />
        </div>

    </div>
</template>

<script>
import { mapActions } from 'vuex'
export default {
    data() {
        return {
            findedUsers: [],
            message: 'начните поиск',
            inputValue: '',
        }
    },

    methods: {
        ...mapActions(['selectUser']),
        inputAction(e) {

            if (e.target.value.indexOf(',')) {
                this.inputValue = e.target.value.split(',')
            } else {
                this.inputValue = e.target.value
            }

            if (this.findedUsers.length == 0 && this.inputValue != '') {
                this.message = 'ничего не найдено'
            } else {
                this.message = 'начните поиск'
            }
            this.findedUsers = []
            this.inputValue.forEach((x) => {

                this.axios.get(`https://jsonplaceholder.typicode.com/users?id=${x}`).then(res => {
                    if (res.data.length != 0) {
                        this.findedUsers.push(res.data[0])
                    } else {
                        this.axios.get(`https://jsonplaceholder.typicode.com/users?username=${x}`).then(res1 => {
                            if (res1.data.length != 0) {
                                this.findedUsers.push(res1.data[0])
                            }
                        })
                    }
                })
            })
        },
        select(e) {
            let findedUser = this.findedUsers.filter(x => x.username === e.target.id)
            this.selectUser(findedUser[0])
        }
    }
}
</script>

<style lang="scss" scoped>
.main_module_sidebar {
    display: flex;
    flex-direction: column;
    width: 30vw;
    min-width: 300px;
    white-space: nowrap;
    padding: 20px;

    .main_module_sidebar_serch {
        display: flex;
        flex-direction: column;
    }

    span {
        font-weight: 600;
        font-size: 16px;
        line-height: 140%;
        color: #333333;
    }

    input {
        box-sizing: border-box;
        background: #FFFFFF;
        padding: 16px 24px;
        font-weight: 400;
        font-size: 14px;
        line-height: 17px;
        color: #76787D;
        border: 1.5px solid #E9ECEF;
        border-radius: 8px;
        width: 100%;
        margin: 18px 0;
    }

    .message {
        font-weight: 400;
        font-size: 14px;
        line-height: 17px;
        color: #76787D;
    }
}

.main_module_sidebar_results {
    padding: 0 5px;
    overflow-y: auto;

    &::-webkit-scrollbar {
        width: 0;
    }
}
</style>