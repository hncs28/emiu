<template>
  <div class="new-page">
    <div class="love-message">
      <h1>Gửi bé iu của anh</h1>
      <p>
        Anh biết thời gian qua, mình không ít lần cãi nhau, có vấn đề với nhau.
      </p>
      <p>
        Anh xin lỗi vì tất cả mọi điều.
      </p>
      <p>
        Anh muốn em biết rằng dù như nào anh vẫn sẽ luôn yêu em hết mình
      </p>
      <p>
        À chúc mừng em ngày 20/10 nhé. Hy vọng em mãi là cô gái bé nhỏ của anh
      </p>
      <p class="signature">Iuuuu emmmm,</p>
      <p class="signature">Ngừi iu đẹp trai của em</p>
    </div>
  </div>
</template>

<script setup>
// Add any JavaScript logic if needed
</script>

<style scoped>
.new-page {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
  width: 100%; /* Full screen height */
  background-color: #f8f1f1; /* Light background color */
  text-align: center;
  padding: 20px;
}

.love-message {
  border: 5px dashed #ff4c4c; /* Dashed border for love decoration */
  padding: 30px;
  border-radius: 15px;
  background: rgba(255, 255, 255, 0.9); /* Slightly transparent background */
  box-shadow: 0 0 20px rgba(0, 0, 0, 0.2);
  max-width: 600px; /* Limit width for larger screens */
  width: 100%;
}

h1 {
  font-family: 'Noto Sans', sans-serif; /* Beautiful script font for the heading */
  color: #d84a45; /* Love-themed color */
  font-size: 2.5em;
  margin-bottom: 15px;
}

p {
  font-size: 1.2em; /* Adjusted font size for better readability */
  color: #333;
  margin: 10px 0;
}

.signature {
  font-weight: bold; /* Emphasized signature */
  font-size: 1.5em; /* Slightly larger signature font */
  color: #ff4c4c; /* Signature color to match the theme */
}

/* Responsive styling for phones */
@media (max-width: 768px) {
  h1 {
    font-size: 2em; /* Slightly smaller heading on small screens */
  }

  p {
    font-size: 1em; /* Adjusted font size for mobile readability */
  }

  .signature {
    font-size: 1.3em; /* Adjust signature size for mobile */
  }

  .love-message {
    padding: 20px; /* Reduce padding on smaller screens */
  }
}
</style>
