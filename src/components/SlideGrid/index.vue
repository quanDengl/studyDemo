<template>
  <div class="grid-box" ref="gridBox">
    <ul>
      <li ref="gridLi" @scroll="nowLeft">
        <span class="grid" v-for="(item, index) in gridData" :key="index">
          <img :src="item.img" alt=""><br>
          <span>{{item.name}}</span>
        </span>
      </li>
    </ul>
    <div class="circle">
      <span ref="circleBoxW">
        <i ref="circleW"></i>
      </span>
    </div>
  </div>
</template>
<script>
export default {
  props: {
    gridData: {
      type: Array,
      default() {
        return [
          {
            id: 0,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 1,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 2,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 3,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 4,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 5,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 6,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          },
          {
            id: 7,
            img: 'https://img.yzcdn.cn/vant/cat.jpeg',
            name: '测试'
          }
        ]
      }
    }
  },
  data() {
    return {
      
    }
  },
  mounted() {
    setTimeout(_ => {
      // 当前屏幕宽度
      const nowScreenW = this.$refs.gridBox.clientWidth;
      // 整个外层盒子的宽度
      const boxSumW = this.$refs.gridLi.scrollWidth;
      // 滑动条盒子的宽度
      const circleBoxW = this.$refs.circleBoxW.offsetWidth;
      // 当前滑动条宽度 = (当前屏幕宽度 / 整个外层盒子的宽度) * 滑动条盒子的宽度
      if(boxSumW < nowScreenW) {
        this.$refs.circleW.style.width = circleBoxW + 'px';
      } else {
        this.$refs.circleW.style.width = Math.ceil((nowScreenW / boxSumW) * circleBoxW) + 'px';
      }
    }, 20);
  },
  methods: {
    nowLeft(e) {
      // 当前滚动距离
      const nowBoxL = e.srcElement.scrollLeft;
      // 整个外层盒子的宽度
      const nowBoxW = e.srcElement.scrollWidth;
      // 滑动条盒子的宽度
      const circleBoxW = this.$refs.circleBoxW.offsetWidth;
      // 当前滑动条滚动距离 = (当前滚动距离 / 整个外层盒子的宽度) * 滑动条盒子的宽度
      this.$refs.circleW.style.left = (nowBoxL / nowBoxW) * circleBoxW + 'px';
    }
  }
}
</script>
<style lang="scss" scoped>
.grid-box {
  ul {
    height: 90px;
    overflow: hidden;
    li {
      overflow-x: scroll;
      white-space: nowrap;
      height: 98px;
      .grid {
        display: inline-block;
        text-align: center;
        padding: 0 8px;
        >img {
          width: 60px;
          height: 60px;
          border-radius: 40px;
        }
      }
    }
  }
  .circle {
    text-align: center;
    >span {
      display: inline-block;
      position: relative;
      width: 80px;
      height: 8px;
      background: #ccc;
      border-radius: 4px;
      >i {
        display: inline-block;
        position: absolute;
        top: 0;
        left: 0;
        width: 20px;
        height: 8px;
        background: #fff;
        border-radius: 4px;
      }
    }
  }
}
</style>