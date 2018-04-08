<template>
    <!-- 结合ElementUI的button组件，改良后button失去焦点后样式不会消失 -->
    <!-- sort-button为可排序按钮 -->

    <div class="sort-button-group">
        <div v-for="(item, index) in sortTagList" :class="['sort-cell', 'diff-width-cell', {'descending':(activeIndex == index&&!sort), 'ascending': (sort == true&&activeIndex == index)}]" @click="switchTag(index, item)">
            <div class="tag">{{ item }}</div>
            <div class="caret-wrapper">
                <i class="sort-caret ascending"></i>
                <i class="sort-caret descending"></i>
            </div>
        </div>
    </div>
</template>
<script>
    export default {
        data() {
            return {
                // sort-button的label列表
                sortTagList: ['毛利额涨幅', '毛利额', '销售额涨幅', '销售额'],
                activeIndex: 3,
                sort: false    //默认值：'descending'
            }
        },
        methods: {
            switchTag(index, item) {
                if(this.activeIndex === index && !this.sort) {
                    this.sort = true;
                }else {
                    this.sort = false;
                }

                this.activeIndex = index;
            }
        }
    }
</script>
<style lang="scss" scoped>
    // 使用sass编写css样式

    // 可排序
    .sort-button-group {
        overflow: hidden;

        .sort-cell {
            float: right;
            margin-right: 10px;
            padding: 5px 10px 5px 0;
            width: 8%;
            text-align: center;
            cursor: pointer;
            border: 1px solid #D9D9D9;
            border-radius: 4px;
            font-size: 14px;
            color: #666666;

            >div {
                display: inline-block;
            }

            .caret-wrapper {
                position: relative;

                .sort-caret {
                    border: 5px solid transparent;
                    position: absolute;
                    left: 0;
                }
                .sort-caret.ascending {
                    border-bottom-color: #D9D9D9;
                    bottom: 6px;
                }
                .sort-caret.descending {
                    border-top-color: #D9D9D9;
                    top: -3px;
                }
            }
        }

        // 点击态
        .sort-cell.ascending {
            .sort-caret.ascending {
                border-bottom-color: #999999;
            }
            .sort-caret.descending {
                border-top-color: #D9D9D9;
            }
        }
        .sort-cell.descending {
            .sort-caret.ascending {
                border-bottom-color: #D9D9D9;
            }
            .sort-caret.descending {
                border-top-color: #999999;
            }
        }
    }
</style>