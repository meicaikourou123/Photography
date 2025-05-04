<template>
  <div class="photo-gallery">
    <h2>📸 我的照片集</h2>
    <div ref="galleryRef" class="gallery">
      <a
        v-for="(img, index) in images"
        :key="index"
        :href="img.full"
        class="photo-link"
      >
        <img :src="img.thumb" :alt="'照片 ' + (index + 1)" />
      </a>
    </div>
  </div>
</template>

<script>
import lightGallery from 'lightgallery';

// 插件可选导入
import lgZoom from 'lightgallery/plugins/zoom';
import lgThumbnail from 'lightgallery/plugins/thumbnail';

// 样式导入
import 'lightgallery/css/lightgallery.css';
import 'lightgallery/css/lg-thumbnail.css';
import 'lightgallery/css/lg-zoom.css';

export default {
  name: 'PhotoGallery',
  data() {
    return {
      images: [
        {
          full: './photos/DSC00814.jpg',
          thumb: './photos/DSC00814.jpg',
        },
        {
          full: './photos/DSC00899.jpg',
          thumb: './photos/DSC00899.jpg',
        },
        {
          full: './photos/DSC01039.jpg',
          thumb: './photos/DSC01039.jpg',
        },
        {
          full: './photos/DSC01063.jpg',
          thumb: './photos/DSC01063.jpg',
        },
        {
          full: './photos/DSC00878.jpg',
          thumb: './photos/DSC00878.jpg',
        },
        {
          full: './photos/DSC00417-2.jpg',
          thumb: './photos/DSC00417-2.jpg',
        },
        {
          full: './photos/DSC00419.jpg',
          thumb: './photos/DSC00419.jpg',
        },
        {
          full: './photos/DSC00692.jpg',
          thumb: './photos/DSC00692.jpg',
        },

        {
          full: './photos/DSC01167.jpg',
          thumb: './photos/DSC01167.jpg',
        },
        {
          full: './photos/DSC01269.jpg',
          thumb: './photos/DSC01269.jpg',
        },
        {
          full: './photos/DSC00611.jpg',
          thumb: './photos/DSC00611.jpg',
        },
        {
          full: './photos/DSC00554.jpg',
          thumb: './photos/DSC00554.jpg',
        },
        {
          full: './photos/DSC00118.jpg',
          thumb: './photos/DSC00118.jpg',
        },
        {
          full: './photos/DSC011990.jpg',
          thumb: './photos/DSC01190.jpg',
        },
        {
          full: './photos/DSC_6301-2.jpg',
          thumb: './photos/DSC_6301-2.jpg',
        },
        // 添加更多照片
      ],
    };
  },
  mounted() {
    lightGallery(this.$refs.galleryRef, {
      plugins: [lgZoom, lgThumbnail],
      speed: 400,
      thumbnail: true,
    });
  },
};
</script>

<style scoped>
.photo-gallery {
  padding:0;
  margin:0;
  padding: 20px;
}
.gallery {
  display: grid;
  grid-template-columns: repeat(5, 1fr); /* 默认桌面显示5列 */
  gap: 6px;
  padding: 6px;
  box-sizing: border-box;
}

/* 手机：小屏幕下 2 列 */
@media (max-width: 600px) {
  .gallery {
    grid-template-columns: repeat(2, 1fr);
  }
}

/* 平板：中等屏幕 3~4 列 */
@media (min-width: 601px) and (max-width: 1024px) {
  .gallery {
    grid-template-columns: repeat(3, 1fr);
  }
}

.gallery img {
  width: 100%;
  height: 100%;
  aspect-ratio: 4 / 3; /* 保持图片比例 */
  object-fit: cover;
  border-radius: 8px;
  cursor: pointer;
  transition: transform 0.3s;
}
.gallery img:hover {
  transform: scale(1.05);
}
</style>
