<script setup>
const props = defineProps({
    list: {
        type: Array,
        required: false,
        default: () => []
    }
})
</script>

<template>
    <div class="list">
        <div class="item" v-for="item in list" :key="item.name">
            <div class="item-left">
                <div class="avatar"></div>
            </div>
            <div class="item-center">
                <p class="name">{{ item.name }}</p>
                <p class="service">
                    <span class="clip">{{ item.service }}</span>
                    <span class="star">{{ item.star }}</span>
                    <span class="order">已单 {{ item.order }}</span>
                </p>
                <p class="rating">{{ item.rating }}</p>
                <el-button style="width: 100%" type="primary">搜索</el-button>
            </div>
            <div class="item-right">
                <div class="item-right-top">
                    <p>
                        <span>${{ item.price }}</span>起
                    </p>
                    <p class="address">距离{{ item.distance }}km</p>
                </div>
                <div class="item-right-bottom">
                    <el-button style="width: 100%" type="defalut">查看位置</el-button>
                </div>
            </div>
        </div>
    </div>
</template>

<style scoped>
.item {
    margin-bottom: 10px;
    display: flex;
    /* 让子元素填满高度 */
    align-items: stretch;
    gap: 1rem;
    /* 卡片加一个阴影效果 */
    box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.2);
    border-radius: 16px;
    padding: 12px;
}

.item-left {
    width: 80px;
    height: 80px;
    display: flex;
    justify-content: end;

    .avatar {
        width: 80px;
        height: 80px;
        border-radius: 16px;
        background-color: gray;
    }
}

.item-center {
    flex: 4;
    display: flex;
    flex-direction: column;
    gap: .4rem;

    .service {
        display: flex;
        gap: .4rem;
        align-items: center;

        .clip {
            background-color: rgb(174, 198, 244);
            color: rgb(76, 118, 225);
            padding: 2px 6px;
            border-radius: 12px;
        }

        .star {
            color: peru;
        }

        .order {
            font-size: 12px;
            color: rgb(154, 158, 154);
        }
    }

    .rating {
        font-size: 14px;
        color: rgb(154, 158, 154);
    }
}

.item-right {
    flex: .8;
    display: flex;
    flex-direction: column;

    .item-right-top {
        flex: 1;
        text-align: end;
        color: rgb(154, 158, 154);

        span {
            color: rgb(226, 101, 101);
            font-size: 18px;
            font-weight: bold;
            margin-right: 2px;
            ;
        }

        .address {
            font-size: 12px;
        }
    }

    .item-right-bottom {
        flex: 1;
        display: flex;
        align-items: end;
    }
}
</style>