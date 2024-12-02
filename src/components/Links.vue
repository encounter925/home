<template>
  <div v-if="siteLinks[0]" class="links">
    <div class="line">
      <Icon size="20">
        <Link />
      </Icon>
      <span class="title">网站列表</span>
    </div>
    <!-- 网站列表 -->
    <Swiper
      v-if="siteLinks[0]"
      :modules="[Pagination, Mousewheel]"
      :slides-per-view="1"
      :space-between="40"
      :pagination="{
        el: '.swiper-pagination',
        clickable: true,
        bulletElement: 'div',
      }"
      :mousewheel="true"
    >
      <SwiperSlide v-for="site in siteLinksList" :key="site">
        <el-row class="link-all" :gutter="20">
          <el-col v-for="(item, index) in site" :span="8" :key="item">
            <div
              class="item cards"
              :style="index < 3 ? 'margin-bottom: 20px' : null"
              @click="jumpLink(item)"
            >
              <Icon size="26">
                <component :is="siteIcon[item.icon]" />
              </Icon>
              <span class="name text-hidden">{{ item.name }}</span>
            </div>
          </el-col>
        </el-row>
      </SwiperSlide>
      <div class="swiper-pagination" />
    </Swiper>
  </div>
</template>

<script setup>
import { Icon } from "@vicons/utils";
// 可前往 https://www.xicons.org 自行挑选并在此处引入
import { Link, Blog, CompactDisc, Cloud, Compass, Book, Fire, Magnet } from "@vicons/fa"; // 注意使用正确的类别
import { mainStore } from "@/store";
import { Swiper, SwiperSlide } from "swiper/vue";
import { Pagination, Mousewheel } from "swiper/modules";
import siteLinks from "@/assets/siteLinks.json";

const store = mainStore();

// 计算网站链接
const siteLinksList = computed(() => {
  const result = [];
  for (let i = 0; i < siteLinks.length; i += 6) {
    const subArr = siteLinks.slice(i, i + 6);
    result.push(subArr);
  }
  return result;
});

// 网站链接图标
const siteIcon = {
  Blog,
  Cloud,
  CompactDisc,
  Compass,
  Book,
  Fire,
  Magnet,
};

// 链接跳转
const jumpLink = (data) => {
  if (data.name === "Clash") {
    ElMessage({
      message: "Clash地址:192.168.31.100:7890",
      grouping: true,
      duration: 4000,
    });

    // 创建临时文本区域以实现复制
    const messageText = "192.168.31.100:7890";
    const textArea = document.createElement("textarea");
    textArea.value = messageText;
    textArea.style.position = "fixed"; // 避免滚动时影响布局
    textArea.style.opacity = "0"; // 隐藏文本区域
    document.body.appendChild(textArea);
    textArea.select();

    try {
      const successful = document.execCommand("copy");
      if (successful) {
        ElMessage({
          message: "Clash地址已成功复制到剪贴板!",
          grouping: true,
          duration: 4000,
        });
      } else {
        ElMessage({
          message: "复制到剪贴板失败",
          grouping: true,
          duration: 4000,
        });
      }
    } catch (err) {
      ElMessage({
          message: "复制到剪贴板时出错！",
          grouping: true,
          duration: 4000,
        });
    }

    // 移除临时文本区域
    document.body.removeChild(textArea);
  }
  else if (data.name === "MC服务器") {
    ElMessage({
      message: "MC 内网:192.168.31.100:25565",
      grouping: true,
      duration: 4000,
    });

    // 创建临时文本区域以实现复制
    const messageText = "192.168.31.100:25565";
    const textArea = document.createElement("textarea");
    textArea.value = messageText;
    textArea.style.position = "fixed"; // 避免滚动时影响布局
    textArea.style.opacity = "0"; // 隐藏文本区域
    document.body.appendChild(textArea);
    textArea.select();

    try {
      const successful = document.execCommand("copy");
      if (successful) {
        ElMessage({
          message: "MC 内网地址已成功复制到剪贴板!",
          grouping: true,
          duration: 4000,
        });
      } else {
        ElMessage({
          message: "复制到剪贴板失败",
          grouping: true,
          duration: 4000,
        });
      }
    } catch (err) {
      ElMessage({
          message: "复制到剪贴板时出错！",
          grouping: true,
          duration: 4000,
        });
    }

    // 移除临时文本区域
    document.body.removeChild(textArea);
  }
  else if (data.name === "MC公网") {
    ElMessage({
      message: "MC 公网:frp-boy.top:17688",
      grouping: true,
      duration: 4000,
    });

    // 创建临时文本区域以实现复制
    const messageText = "frp-boy.top:17688";
    const textArea = document.createElement("textarea");
    textArea.value = messageText;
    textArea.style.position = "fixed"; // 避免滚动时影响布局
    textArea.style.opacity = "0"; // 隐藏文本区域
    document.body.appendChild(textArea);
    textArea.select();

    try {
      const successful = document.execCommand("copy");
      if (successful) {
        ElMessage({
          message: "MC 公网地址已成功复制到剪贴板!",
          grouping: true,
          duration: 4000,
        });
      } else {
        ElMessage({
          message: "复制到剪贴板失败",
          grouping: true,
          duration: 4000,
        });
      }
    } catch (err) {
      ElMessage({
          message: "复制到剪贴板时出错！",
          grouping: true,
          duration: 4000,
        });
    }

    // 移除临时文本区域
    document.body.removeChild(textArea);
  }
  else if (data.name === "无名杀服务器") {
    ElMessage({
      message: "无名杀服务器:124.71.113.247:32770",
      grouping: true,
      duration: 4000,
    });

    // 创建临时文本区域以实现复制
    const messageText = "124.71.113.247:32770";
    const textArea = document.createElement("textarea");
    textArea.value = messageText;
    textArea.style.position = "fixed"; // 避免滚动时影响布局
    textArea.style.opacity = "0"; // 隐藏文本区域
    document.body.appendChild(textArea);
    textArea.select();

    try {
      const successful = document.execCommand("copy");
      if (successful) {
        ElMessage({
          message: "无名杀服务器地址已成功复制到剪贴板!",
          grouping: true,
          duration: 4000,
        });
      } else {
        ElMessage({
          message: "复制到剪贴板失败",
          grouping: true,
          duration: 4000,
        });
      }
    } catch (err) {
      ElMessage({
          message: "复制到剪贴板时出错！",
          grouping: true,
          duration: 4000,
        });
    }

    // 移除临时文本区域
    document.body.removeChild(textArea);
  }
  else {
    window.open(data.link, "_blank");
  }
};

onMounted(() => {
  console.log(siteLinks);
});
</script>

<style lang="scss" scoped>
.links {
  .line {
    margin: 2rem 0.25rem 1rem;
    font-size: 1.1rem;
    display: flex;
    align-items: center;
    animation: fade 0.5s;
    .title {
      margin-left: 8px;
      font-size: 1.15rem;
      text-shadow: 0 0 5px #00000050;
    }
  }
  .swiper {
    left: -10px;
    width: calc(100% + 20px);
    padding: 5px 10px 0;
    z-index: 0;
    .swiper-slide {
      height: 100%;
    }
    .swiper-pagination {
      margin-top: 12px;
      display: flex;
      flex-direction: row;
      align-items: center;
      justify-content: center;
      :deep(.swiper-pagination-bullet) {
        background-color: #fff;
        width: 20px;
        height: 4px;
        margin: 0 4px;
        border-radius: 4px;
        opacity: 0.2;
        transition: opacity 0.3s;
        &.swiper-pagination-bullet-active {
          opacity: 1;
        }
        &:hover {
          opacity: 1;
        }
      }
    }
  }
  .link-all {
    height: 220px;
    .item {
      height: 100px;
      width: 100%;
      display: flex;
      align-items: center;
      flex-direction: row;
      justify-content: center;
      padding: 0 10px;
      animation: fade 0.5s;

      &:hover {
        transform: scale(1.02);
        background: rgb(0 0 0 / 40%);
        transition: 0.3s;
      }

      &:active {
        transform: scale(1);
      }

      .name {
        font-size: 1.1rem;
        margin-left: 8px;
      }
      @media (min-width: 720px) and (max-width: 820px) {
        .name {
          display: none;
        }
      }
      @media (max-width: 720px) {
        height: 80px;
      }
      @media (max-width: 460px) {
        flex-direction: column;
        .name {
          font-size: 1rem;
          margin-left: 0;
          margin-top: 8px;
        }
      }
    }
    @media (max-width: 720px) {
      height: 180px;
    }
  }
}
</style>
