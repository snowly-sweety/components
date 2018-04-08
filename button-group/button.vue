<template>
    <!-- 结合ElementUI的button组件，改良后button失去焦点后样式不会消失 -->
    <!-- size可选项：medium / small / mini -->
    <!-- plain：是否为朴素按钮(ElementUI自带) -->
    <div class="button-group">
        <el-button size="small" plain
            v-for="(item, index) in btnList"
            :key="index"
            :class="[active == index ? 'active':'']"
            @click="switchSelected(active, index)"
        >{{item}}</el-button>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                // button的label列表
                btnList: ['自选对比时间', '同比', '环比'],
                active: 2,
            }
        },
        methods: {
            switchSelected: function(active, index) {
                this.active = index;
            }
        }
    }
</script>
<style lang="scss" scoped>
    // 使用sass编写css样式
    // 不可排序button
    .button-group{
        >button{
            float: right;
            margin-right: 10px;
            margin-left: 0;

            &:first-child {
                margin-right: 0;
            }
            &:hover {
                @extend .active;
            }
            &:focus {
                @extend .active;
            }
        }
    }
</style>