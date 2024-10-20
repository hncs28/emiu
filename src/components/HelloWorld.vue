<template>
  <link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@700&family=Dancing+Script:wght@600&display=swap" rel="stylesheet">
  <div class="container">
    <h1 v-if="showImage" class="title">Kỷ niệm tụi mìnhhhh</h1>
    <img v-if="showImage" :src="currentImage" alt="Displayed Image" class="center-image" />
    <p v-if="showImage" class="image-text">{{ currentText }}</p>
    <button v-if="!showImage" @click="playMusic" class="play-button">Ấn đây nài</button>
    <div class="hearts-container" v-if="showHearts">
      <div v-for="heart in hearts" :key="heart.id" class="heart" :style="heartStyle(heart)"></div>
    </div>
  </div>
</template>

<script>
import { ref } from 'vue';
import { useRouter } from 'vue-router';
import image1 from '../assets/image1.png';
import image2 from '../assets/image2.PNG';
import image3 from '../assets/image3.png';
import image4 from '../assets/image4.PNG';
import image5 from '../assets/image5.PNG';
import image6 from '../assets/image6.PNG';
import image7 from '../assets/image7.PNG';
import image8 from '../assets/image8.PNG';
import image9 from '../assets/image9.JPG';
import image10 from '../assets/image10.PNG';
import image11 from '../assets/image11.png';
import image12 from '../assets/image12.png';
import backgroundMusic from '../assets/oimatriu.mp3';

export default {
  setup() {
    const router = useRouter();
    const showImage = ref(false);
    const showHearts = ref(false);
    const currentImage = ref('');
    const currentText = ref('');
    const hearts = ref([]);

    const images = [image1, image2, image3, image4, image5, image6, image7, image8, image9, image10, image11, image12];
    const texts = [
      'Lần đầu đi chơi nà',
      'Lần đầu cùng ăn lỏu',
      'Đi quán tối tối có con mòe',
      'Ảnh của ẻm ấy',
      'Rồi mình chính thức iu nhauuu',
      'Zẫn là đi ăn',
      'Món quà sinh nhật đầu tiênnn',
      'Đi chơiiii',
      'Thức đêm bảo đi ngủ hong ngheee',
      'Đi xem phim cùng nhau lần đầu nà',
      'Đi Hồ Têii',
      'Vẫn nà đi Hồ Têii',
    ];

    let currentIndex = 0;
    let interval = null;

    const generateHeart = () => {
      hearts.value.push({
        id: Date.now(),
        size: Math.random() * 50 + 10,
        left: Math.random() * 100,
        duration: Math.random() * 5 + 3,
      });
      setTimeout(() => {
        hearts.value.shift();
      }, 5000);
    };

    const playMusic = () => {
      const audio = new Audio(backgroundMusic);
      audio.currentTime = 18;
      audio.play();

      showImage.value = true;
      currentIndex = 0;
      currentImage.value = images[currentIndex];
      currentText.value = texts[currentIndex];

      interval = setInterval(() => {
        currentIndex = (currentIndex + 1) % images.length;
        currentImage.value = images[currentIndex];
        currentText.value = texts[currentIndex];
      }, 3000);

      showHearts.value = true;
      setInterval(generateHeart, 500);

      audio.addEventListener('ended', () => {
        clearInterval(interval);
        showImage.value = false;
        showHearts.value = false;
        router.push({ name: 'NewPage' });
      });

      setTimeout(() => {
        audio.pause();
        clearInterval(interval);
        showImage.value = false;
        showHearts.value = false;
        router.push({ name: 'NewPage' });
      }, 57000);
    };

    const heartStyle = (heart) => ({
      width: `${heart.size}px`,
      height: `${heart.size}px`,
      left: `${heart.left}%`,
      animationDuration: `${heart.duration}s`,
    });

    return {
      showImage,
      currentImage,
      currentText,
      playMusic,
      showHearts,
      hearts,
      heartStyle,
    };
  },
};
</script>

<style scoped>
.container {
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  height: 100vh;
  background: radial-gradient(circle at center, #000000, #000);
  color: white;
  overflow: hidden;
  position: relative;
}

.title {
  font-family: 'Be Vietnam Pro', sans-serif;
  color: #ff79c6;
  font-size: 3rem;
  font-weight: 700;
  margin-bottom: 20px;
  text-align: center;
  letter-spacing: 2px;
  animation: fadeIn 1s ease-in-out;
}

.center-image {
  max-width: 250px;
  max-height: 400px;
  border-radius: 10px;
  animation: fadeIn 2s ease-in-out;
}

.image-text {
  margin: 10px 0;
  text-align: center;
  font-size: 1rem;
  color: #ff79c6;
  animation: fadeIn 3s ease-in-out;
}

.play-button {
  box-shadow: -4px 8px 0px 0px #7416ab;
  background: linear-gradient(to bottom, #ff7aaf 5%, #9f39e3 100%);
  background-color: #ff7aaf;
  border: 2px solid #8e34c2;
  display: inline-block;
  cursor: pointer;
  color: #ffffff;
  font-family: Verdana;
  font-size: 17px;
  font-weight: bold;
  padding: 13px 45px;
  text-decoration: none;
  text-shadow: 0px 3px 0px #9254cc;
  animation: bounce 2s infinite;
}

.play-button:hover {
  background: linear-gradient(to bottom, #9f39e3 5%, #ff7aaf 100%);
}

.hearts-container {
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  overflow: hidden;
}

.heart {
  position: absolute;
  bottom: -50px;
  width: 50px;
  height: 50px;
  background: rgba(255, 182, 193, 0.9);
  border-radius: 50%;
  animation: floatUp 5s linear infinite;
  transform: scale(0.8);
}

@keyframes floatUp {
  0% {
    transform: translateY(0) scale(0.8);
  }
  100% {
    transform: translateY(-100vh) scale(1);
  }
}

@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}

@keyframes bounce {
  0%, 100% {
    transform: translateY(0);
  }
  50% {
    transform: translateY(-10px);
  }
}
</style>
