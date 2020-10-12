<template>
<div>
    <el-row>
        <el-col :style="'height:'+fullHeight+'px;'">
            <img class="img-responsive" src='https://bytethink.oss-cn-shanghai.aliyuncs.com/demo/result/%E9%9A%A7%E9%81%93%E9%AB%98%E5%88%86%E8%BE%A8%E7%8E%87%E5%B9%B3%E9%93%BA%E5%9B%BE/1%2020.bmp' />
        </el-col>
    </el-row>

    <el-row class="buttom_btn">
        <el-button icon="iconfont el-icon-my-quanping" circle></el-button>
        <el-button icon="iconfont el-icon-my-pen" circle></el-button>
        <el-button type="info" icon="iconfont el-icon-my-drag" circle></el-button>
        <el-button type="warning" icon="iconfont el-icon-my-eraser" circle></el-button>
        <el-button type="danger" icon="iconfont el-icon-my-tuodong" circle></el-button>
        <el-button type="warning" icon="iconfont el-icon-my-small" circle></el-button>
    </el-row>

</div>
</template>

<script>
import actionbar from '@/components/toolbar/actionbar';
import drawbar from '@/components/toolbar/drawbar';
import pannel from '@/components/pannel/pannel';
export default {
    components: {
        actionbar,
        drawbar,
        pannel
    },
    data() {
        return {
            name: "penglv",
            fullHeight: document.documentElement.clientHeight - 80,
        }
    },
    watch: {
        fullHeight(val) { //监控浏览器高度变化
            if (!this.timer) {
                this.fullHeight = val
                this.timer = true
                let that = this
                setTimeout(function () {
                    that.timer = false
                }, 400)
            }

        }
    },
    mounted() {
        this.get_bodyHeight()
    },
    methods: {
        get_bodyHeight() { //动态获取浏览器高度
            const that = this
            window.onresize = () => {
                return (() => {
                    window.fullHeight = document.documentElement.clientHeight
                    that.fullHeight = window.fullHeight
                })()
            }
        }
    }

}
</script>

<style scoped>
.img-responsive {
    display: inline-block;
    max-height: 100%;

}

.buttom_btn {
    height: 70px;
    margin-top: 10px;
}
</style>
