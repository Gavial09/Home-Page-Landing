<template>
  <div class="home-container">
    <div class="bg-light">
      <h2 class="h4">Initialization complete.</h2>
      <p class="mb-0">Welcome to the Landing Zone.</p>
    </div>
  </div>
</template>

<style scoped>
.home-container {
  min-height: calc(100vh - 56px);
  width: 100%;
  background-color: #1a1a1a;;
  background-image: url('/Rhodes_Island_Bridge.png');
  background-size: 100% auto;
  background-position: center;
  background-repeat: no-repeat;
  display: flex;
  flex-direction: column;
  align-items: stretch;
  margin: 0;
  padding: 0;
  position: absolute;
  top: 56px;
  left: 0;
  right: 0;
  bottom: 0;
  overflow: hidden;
}

.bg-light {
  background-color: rgba(255, 255, 255, 0.9) !important;
  width: 100%;
  padding: 1rem;
  text-align: center;
  font-weight: bold;
}

.h4 {
  font-weight: bold;
}
</style>