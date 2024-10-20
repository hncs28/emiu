<template>
  <link href="https://fonts.googleapis.com/css2?family=Be+Vietnam+Pro:wght@700&display=swap" rel="stylesheet">
  <div class="container">
    <h1 v-if="showImage">Kỷ niệm tụi mìnhhhh</h1>
    <img v-if="showImage" :src="currentImage" alt="Displayed Image" class="center-image" />
    <p v-if="showImage" class="image-text">{{ currentText }}</p> 
    <button v-if="!showImage" @click="playMusic" class="play-button">Ấn đây nài</button>
  </div>
</template>

<script>
import { ref } from 'vue'; 
import { useRouter } from 'vue-router';

// Import images
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
    const currentImage = ref('');
    const currentText = ref('');
    
    // Array of images and corresponding texts
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

    const playMusic = () => {
      const audio = new Audio(backgroundMusic); // Your music file
      audio.currentTime = 18; // Start the audio at the 18-second mark
      audio.play();

      showImage.value = true; // Show the image when music plays
      currentIndex = 0; // Reset index
      currentImage.value = images[currentIndex]; // Set the initial image
      currentText.value = texts[currentIndex]; // Set the initial text

      // Automatically change the image and text every 5 seconds
      interval = setInterval(() => {
        currentIndex = (currentIndex + 1) % images.length; // Loop through images
        currentImage.value = images[currentIndex];
        currentText.value = texts[currentIndex]; 
      }, 3000); 

      
      audio.addEventListener('ended', () => {
        clearInterval(interval); // Clear the interval to stop changing images
        showImage.value = false; // Hide the image
        router.push({ name: 'NewPage' }); // Navigate to the new page
      });

      // Set a timeout to navigate to the new page after 57 seconds
      setTimeout(() => {
        audio.pause(); // Pause the music
        clearInterval(interval); // Clear the interval
        showImage.value = false; // Hide the image
        router.push({ name: 'NewPage' }); // Navigate to the new page
      }, 57000); // 57 seconds
    };

    return {
      showImage,
      currentImage,
      currentText,
      playMusic,
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
  height: 100%; 
  width: 100%;
  background-color: black; /* Black background */
  color: white;
}

.center-image {
  max-width: 250px; /* Resize image to be smaller */
  max-height: 400px;
  border-radius: 10px; /* Optional: round image corners */
}

h1 {
  font-family: 'Be Vietnam Pro', sans-serif; /* Use beautiful Vietnamese font */
  color: #ff79c6; /* Soft pink color for contrast with black background */
  font-size: 3rem; /* Adjust font size */
  font-weight: 700; /* Make the text bold */
  margin-bottom: 20px;
  text-align: center;
  letter-spacing: 2px;
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
}

.play-button:hover {
  background: linear-gradient(to bottom, #9f39e3 5%, #ff7aaf 100%);
  background-color: #9f39e3;
}

.play-button:active {
  position: relative;
  top: 1px;
}

.image-text {
  margin: 10px 0;
  text-align: center;
  font-size: 1rem;
  color: #ff79c6; /* Match text color with h1 */
}
</style>