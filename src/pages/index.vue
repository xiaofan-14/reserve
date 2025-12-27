<script setup lang="ts">
import { ref } from 'vue'

const value = ref('')

const options = [
    {
        value: 'user',
        label: '用户登录',
        to: '/user-login'
    },
    {
        value: 'worker',
        label: '服务商登录',
        to: '/server-login'
    },
    {
        value: 'admin',
        label: '管理员登录',
        to: '/admin-login'
    },
]
</script>

<template>
    <el-header class="app-header">
        <div class="left">维修预约系统</div>
        <div class="right">
            <el-select v-model="value" placeholder="登录" style="width: 100px;">
                <el-option v-for="item in options" :key="item.value" :label="item.label" :value="item.value" />
            </el-select>
        </div>
    </el-header>
    <el-main class="main-content">
        <div class="main-bg">
            <div class="main-left"></div>
        </div>
    </el-main>

</template>

<style scoped>
.app-header {
    background-color: white;
    color: #333;
    position: fixed;
    top: 0;
    left: 0;
    width: 100%;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

.main-content {
    padding: 0;
    margin-top: 60px;
}
</style>