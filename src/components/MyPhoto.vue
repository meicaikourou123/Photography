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
          full: '/photos/DSC00814.jpg',
          thumb: '/photos/DSC00814.jpg',
        },
        {
          full: '/photos/DSC00899.jpg',
          thumb: '/photos/DSC00899.jpg',
        },
        {
          full: '/photos/DSC01039.jpg',
          thumb: '/photos/DSC01039.jpg',
        },
        {
          full: '/photos/DSC01063.jpg',
          thumb: '/photos/DSC01063.jpg',
        },
        {
          full: '/photos/DSC00878.jpg',
          thumb: '/photos/DSC00878.jpg',
        },
        {
          full: '/photos/DSC00417-2.jpg',
          thumb: '/photos/DSC00417-2.jpg',
        },
        {
          full: '/photos/DSC00419.jpg',
          thumb: '/photos/DSC00419.jpg',
        },
        {
          full: '/photos/DSC00692.jpg',
          thumb: '/photos/DSC00692.jpg',
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
  height: 80vh;
  display: grid;
  grid-template-columns: repeat(4, 1fr); /* 每行6张图 */
  grid-template-rows: repeat(2, 1fr);    /* 共4行 */
  gap: 6px;
  padding: 6px;
  box-sizing: border-box;
  overflow: hidden;
}

.gallery img {
  width: 300px;

  overflow: hidden;
  border-radius: 8px;
  cursor: pointer;
  transition: transform 0.3s;
}
.gallery img:hover {
  transform: scale(1.05);
}
</style>
