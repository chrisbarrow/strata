<template>
  <div>
    <!-- <div class="messages">
      <p :class="{ active: activeMessage === 0 }">
        Built for<br />People and Brands<br />on a mission.
      </p>
      <p :class="{ active: activeMessage === 1 }">
        Different Expertise.<br />Shared Energy.
      </p>
    </div> -->
    <div class="gradient-bg">
      <svg xmlns="http://www.w3.org/2000/svg">
        <defs>
          <filter id="goo">
            <feGaussianBlur
              in="SourceGraphic"
              stdDeviation="10"
              result="blur"
            />
            <feColorMatrix
              in="blur"
              mode="matrix"
              values="1 0 0 0 0  0 1 0 0 0  0 0 1 0 0  0 0 0 18 -8"
              result="goo"
            />
            <feBlend in="SourceGraphic" in2="goo" />
          </filter>
        </defs>
      </svg>
      <div class="gradients-container">
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
        <div class="orbit"><div class="box"></div></div>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
const activeMessage = ref(-1);

const nextMessage = () => {
  activeMessage.value = (activeMessage.value + 1) % 2; // Assuming there are 2 messages
};

onMounted(() => {
  setTimeout(() => {
    activeMessage.value = 0;
    setInterval(nextMessage, 5000); // Change message every 5 seconds
  }, 1000); // Show the first message immediately
  //setInterval(nextMessage, 5000); // Change message every 5 seconds
});
</script>

<style lang="css">
.messages {
  position: fixed;
  z-index: 10;
  width: 100%;
  height: 100%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
  text-align: center;

  p {
    position: absolute;
    width: 100%;
    height: 100%;
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    text-align: center;
    font-family: 'Gibson', sans-serif;
    font-weight: 700;
    text-transform: uppercase;
    font-size: 5vw;
    opacity: 0;
    transition: all 0.5s ease-in-out;
    transform: translateY(20px);
    line-height: 0.8;

    &.active {
      opacity: 1;
      transform: translateY(0);
    }
  }
}
</style>
