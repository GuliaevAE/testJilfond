<script setup>
import img from '../assets/Img.svg'
</script>
<template>
    <div class="main_module_info" :class="{ empyArray: getSelectedUser === null }">
        <span v-if="getSelectedUser === null">Выберите сотрудника, чтобы посмотреть его профиль</span>
        <div v-else class="main_module_info_user">
            <div class="main_module_info_user_img item" style="">
                <img :src="img" alt="img">
            </div>
            <div class="main_module_info_user_description item">
                <div class="name">{{ getSelectedUser.name }}</div>
                <div class="subtitles">email: <span>{{ getSelectedUser.email }}</span></div>
                <div class="subtitles">phone: <span>{{ getSelectedUser.phone }}</span></div>
                <div class="subtitles myself">О себе:</div>
                <div class="myself">
                    Lorem ipsum dolor sit amet, consectetur adipiscing elit, sed do eiusmod tempor incididunt ut labore
                    et dolore magna aliqua. Ut enim ad minim veniam, quis nostrud exercitation ullamco laboris nisi ut
                    aliquip ex ea commodo consequat. Duis aute irure dolor in reprehenderit in voluptate velit esse
                    cillum dolore eu fugiat nulla pariatur. Excepteur sint occaecat cupidatat non proident, sunt in
                    culpa qui officia deserunt mollit anim id est laborum.
                </div>
            </div>
        </div>


    </div>
</template>


<script>
import { mapGetters } from 'vuex'
export default {
    computed: {
        ...mapGetters([
            'getSelectedUser',
        ])
    },
}
</script>

<style lang="scss" scoped>
.main_module_info {
    display: flex;
    width: 100%;
    font-size: 14px;
    line-height: 17px;
    color: #76787D;
    padding: 3% 3%;
    border-left: 1px solid #E0E0E0;
    overflow-y: auto;

    &::-webkit-scrollbar {
        width: 0;
    }
}

.empyArray {
    justify-content: center;
    align-items: center;
    padding-top: 0;
}

.main_module_info_user {
    display: flex;

    .item {
        margin: 0 2%;
        width: 50%;

        img {
            width: 100%;
        }
    }
}

.main_module_info_user_description {
    display: flex;
    flex-direction: column;

    .name {
        font-weight: 600;
        font-size: 16px;
        line-height: 140%;
        color: #000000;
    }

    .subtitles {
        font-weight: 600;
        font-size: 14px;
        line-height: 140%;
        color: #333333;
        margin: 5px 0;

        span {
            color: #76787D;
            font-weight: 500;
        }

        .myself {
            margin: 15px 0;
        }
    }

    .myself {
        margin-top: 20px;
        font-weight: 400;
        font-size: 14px;
        line-height: 17px;
        color: #76787D;

    }
}


@media (max-width: 900px) {
    .main_module_info_user {
        flex-direction: column;

        .item {
            width: 100%;
        }
    }
}
</style>