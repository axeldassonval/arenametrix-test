<template>
  <div>
    <nav class="kl-navbar content-wrapper">
      <a href="https://arenametrix.com">
        <img
          src="https://arenametrix.com/hubfs/Arenametrix_theme_aug2023/Logo-Arenametrix-%C3%A9criture-verte.png"
          alt="Arenametrix"
          style="max-width: 100%; height: auto"
          class="kl-navbar__logo"
        />
      </a>
    </nav>
  </div>
</template>

<script setup></script>

<style scoped>
.content-wrapper {
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 0 20px;
  background-color: #fff;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.1);
}
.kl-navbar__logo {
  width: 65px;
  display: block;
  margin-right: 42px;
}
.kl-navbar {
  background-color: #fff;
  height: 60px;
  box-shadow: 0 2px 4px 0 rgba(0, 0, 0, 0.1);
  position: fixed;
  top: 0;
  left: 0;
  right: 0;
  z-index: 1000;
  padding: 0 20px;
  display: flex;
  justify-content: space-between;
  align-items: center;
  width: 100%;
  min-height: 100px;
  transition: all 0.3s;
}
</style>
