<script setup>
import { ref, watch } from 'vue'
import { Search } from '@element-plus/icons-vue'
import WorkerList from '../components/WorkerList.vue'

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

const list = [
    {
        name: '张师傅',
        service: 'AC',
        star: 4.9,
        order: 128,
        rating: '10年空调维修经验，擅长格力、美的等品牌，持证上岗。',
        price: 150,
        distance: 1.2,
        type: 'air-conditioner'
    },
    {
        name: '李师傅',
        service: 'Washing Machine',
        star: 4.8,
        order: 200,
        rating: '8年洗衣机维修经验，熟悉各种品牌，服务态度好。',
        price: 120,
        distance: 0.8,
        type: 'washing-machine'
    },
    {
        name: '王师傅',
        service: 'Refrigerator',
        star: 4.7,
        order: 150,
        rating: '5年冰箱维修经验，技术过硬，价格合理。',
        price: 180,
        distance: 2.0,
        type: 'refrigerator'
    },
    {
        name: '赵师傅',
        service: 'Heater',
        star: 4.9,
        order: 300,
        rating: '12年热水器维修经验，响应迅速，客户好评如潮。',
        price: 200,
        distance: 1.5,
        type: 'heater'
    }
]

const filterList = ref(list)

watch(value2, (newVal) => {
    if (newVal === 'all') {
        filterList.value = list;
    } else {
        filterList.value = list.filter(item => item.type === newVal);
    }
});

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
    <el-main>
        <div class="main-content">
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
        </div>
        <div class="content">
            <div class="worker-list">
                <!-- 技师列表展示区域 -->
                <p class="worker-title">
                    推荐维修师
                </p>
                <WorkerList :list="filterList" />
            </div>
            <div class="map">
                <p class="worker-title">
                    周边服务分布
                </p>
                <div style="width: 400px; height: 400px; background: #ccc;"></div>
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
    border-bottom: 1px solid #e8e8e8;
    z-index: 999;
}

.main-content {
    padding: 0;
    margin-top: 40px;
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

.content {
    display: flex;
    gap: 1rem;
}

.map {
    margin-top: 16px;
    display: flex;
    flex-direction: column;
    gap: 1rem;
 }

.worker-list {
    flex: 1;
    margin-top: 16px;
}

.worker-title {
    font-size: 24px;
    font-weight: bold;
}
</style>