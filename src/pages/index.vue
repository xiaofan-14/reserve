<script setup lang="ts">
import { ref } from 'vue'
import { Search } from '@element-plus/icons-vue'

const value = ref('')
const value2 = ref('')
const input3 = ref('')
const input = ref('')
const select = ref('')

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
const options2 = [
    {
        value: 'all',
        label: '全部分类',
    },
    {
        value: 'air-conditioner',
        label: '空调维修',
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
            <div class="main-left">
                <p class="main-title">专业家电维修，一键预约</p>
                <p class="main-subtitle">认证师傅 · 价格透明 · 售后无忧</p>
                <div class="main-search">
                    <el-input v-model="input" style="width: 240px" placeholder="Please input">
                        <template #prepend>
                            <Search style="width: 1em; height: 1em; color: #ccc;" />
                        </template>
                    </el-input>
                    <div style="display: flex; gap: 16px;">
                        <el-select v-model="value2" placeholder="全部分类" style="width: 100px;">
                            <el-option v-for="item in options2" :key="item.value" :label="item.label"
                                :value="item.value" />
                        </el-select>
                        <el-button type="primary">搜索</el-button>
                    </div>
                </div>
            </div>
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
    height: 300px;
}

.main-bg {
    width: 100%;
    height: 100%;
    border-radius: 15px;
    background:
        linear-gradient(rgba(0, 0, 0, .4), rgba(0, 0, 0, .4)),
        url('../assets/bg.png') center / cover no-repeat;

    /* 
        用一张不变形、不平铺、以中心为焦点的图片，铺满整个容器
    */
    /* background-image: url('../assets/bg.png');
    background-size: cover;
    background-position: center;
    background-repeat: no-repeat; */

    display: flex;
}

.main-left {
    color: white;
    font-weight: bold;
    width: 50%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-left: 30px;
}

p {
    margin: 0;
    width: 100%;
}

.main-title {
    font-size: 36px;
}

.main-subtitle {
    font-size: 18px;
    margin-top: 10px;
    color: rgb(205, 203, 203);
}

.main-search {
    margin-top: 14px;
    box-sizing: border-box;
    padding: 10px 16px;
    width: 100%;
    background: white;
    border-radius: 100px;
    display: flex;
    align-items: center;
    justify-content: space-between;
}

::v-deep(.el-input-group__prepend) {
    padding: 10px;
    box-shadow: none;
}
</style>