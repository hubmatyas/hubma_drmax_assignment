<template>
  <div class="spinner-wrapper">
    <svg class="spinner" width="65px" height="65px" viewBox="0 0 66 66">
       <circle class="spinner-circle" fill="none" stroke-width="6" stroke-linecap="round" cx="33" cy="33" r="30"></circle>
    </svg>
  </div>
</template>

<style scoped>
.spinner-wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
  height: 100%;
}
.spinner {
  animation: rotator 1.4s linear infinite;
}

@keyframes rotator {
  0% {
    transform: rotate(0deg);
  }

  100% {
    transform: rotate(270deg);
  }
}

.spinner-circle {
  stroke-dasharray: 187;
  stroke-dashoffset: 0;
  transform-origin: center;
  animation:
    dash 1.4s ease-in-out infinite,
    colors 5.6s ease-in-out infinite;
}

@keyframes colors {
  0% {
    stroke: #4285F4;
  }

  25% {
    stroke: #DE3E35;
  }

  50% {
    stroke: #F7C223;
  }

  75% {
    stroke: #1B9A59;
  }

  100% {
    stroke: #4285F4;
  }
}

@keyframes dash {
  0% {
    stroke-dashoffset: 187;
  }

  50% {
    stroke-dashoffset: 46.75;
    transform: rotate(135deg);
  }

  100% {
    stroke-dashoffset: 187;
    transform: rotate(450deg);
  }
}
</style>