<script setup>
import miniImg from '../assets/miniImg.svg'

</script>

<template>
    <div class="minicard">
        <img :src="miniImg" alt="">
        <div class="minicard_description"
            :class="{ selected: getSelectedUser && (item.username == getSelectedUser.username || item.id == getSelectedUser.id) }"
            :id="item.username">
            <span class="name" :id="item.username">{{ item.username }}</span>
            <span class="email" :id="item.username">{{ item.email }}</span>
        </div>
    </div>

</template>

<script>
import { mapActions, mapGetters } from 'vuex'
export default {
    props: ['item'],
    computed: {
        ...mapGetters([
            'getSelectedUser',
        ])
    },

}

</script>

<style lang="scss" scoped>
.minicard {
    width: 100%;
    display: flex;
    margin: 20px 0;
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.1);
    border-radius: 10px;
}

.selected {
    background: #E0E0E0;
}

.minicard_description {
    width: 100%;
    padding: 10px 5px;
    border-radius: 0 10px 10px 0;
    display: flex;
    justify-content: center;
    flex-direction: column;
    font-weight: 600;
    font-size: 14px;
    line-height: 17px;

    .name {

        color: #333333;
    }

    .email {


        color: #76787D;
    }
}
</style>