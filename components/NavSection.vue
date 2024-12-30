<script setup>
const scrollToSection = inject('scrollToSection')

const handleScroll = () => {
  scrollToSection('home')
}
</script>

<template>
  <div class="card">
    <ul>
      <li class="iso-pro">
        <span></span>
        <span></span>
        <span></span>
        <a @click.prevent="handleScroll">
          <HomeIcon class="svg" />
        </a>
        <div class="text">Home</div>
      </li>
      <li class="iso-pro">
        <span></span>
        <span></span>
        <span></span>
        <a href="https://web.facebook.com/nyjaaaaa" target="_blank">
          <FacebookIcon class="svg" />
        </a>
        <div class="text">Facebook</div>
      </li>
      <li class="iso-pro">
        <span></span>
        <span></span>
        <span></span>
        <a>
          <ModeToggle class="svg" />
        </a>
        <div class="text">Theme</div>
      </li>
      <li class="iso-pro">
        <span></span>
        <span></span>
        <span></span>
        <a href="https://github.com/ny-ja" target="_blank">
          <GithubIcon class="svg" />
        </a>
        <div class="text">Github</div>
      </li>
      <li class="iso-pro">
        <span></span>
        <span></span>
        <span></span>
        <a href="https://www.linkedin.com/in/johnny-ermio-600333329" target="_blank">
          <LinkedinIcon class="svg" />
        </a>
        <div class="text">LinkedIn</div>
      </li>
    </ul>
  </div>
</template>

<style scoped>
.card {
  max-width: fit-content;
  padding: 0px 8px 0px 8px;
  border-radius: 30px;
  display: flex;
  flex-direction: row;
  align-content: center;
  justify-content: center;
  gap: 0.5rem;
  backdrop-filter: blur(10px);
  box-shadow: inset 0 0 12px rgba(255, 255, 255, 0.192),
    inset 0 0 3px rgba(255, 255, 255, 0.274), 0 3px 3px rgba(0, 0, 0, 0.164);
  transition: 0.5s;
}

.card:hover {
  animation: ease-out 5s;
  background: rgba(173, 173, 173, 0.05);
}

.card ul {
  padding: 0.5rem;
  display: flex;
  list-style: none;
  gap: 0.5rem;
  align-items: center;
  justify-content: center;
  align-content: center;
  flex-wrap: nowrap;
  flex-direction: row;
}

.card ul li {
  cursor: pointer;
}

.svg {
  transition: all 0.3s;
  padding: 0.5rem;
  height: 36px;
  width: 36px;
  border-radius: 100%;
  color: #14b8a6;
  fill: currentColor;
  box-shadow: inset 0 0 12px rgba(255, 255, 255, 0.3),
    inset 0 0 3px rgba(255, 255, 255, 0.5), 0 3px 3px rgba(0, 0, 0, 0.164);
}

.text {
  opacity: 0;
  border-radius: 5px;
  padding: 3px;
  color: #14b8a6;
  transition: all 0.3s;
  background-color: rgba(255, 255, 255, 0.3);
  position: absolute;
  z-index: 9999;
  box-shadow: -3px 0 1px rgba(153, 153, 153, 0.2),
    -6px 0 1px rgba(153, 153, 153, 0.2),
    inset 0 0 12px rgba(255, 255, 255, 0.3),
    inset 0 0 3px rgba(255, 255, 255, 0.5), 0 3px 3px rgba(0, 0, 0, 0.082);
}

.iso-pro {
  transition: 0.5s;
}

.iso-pro:hover a>.svg {
  transform: translate(8px, -8px);
  border-radius: 100%;
}

.iso-pro:hover .text {
  opacity: 1;
  transform: translate(12px, -1px) skew(-5deg);
}

.iso-pro:hover .svg {
  transform: translate(3px, -3px);
}

.iso-pro span {
  opacity: 0;
  position: absolute;
  color: #1877f2;
  border-color: #1877f2;
  box-shadow: inset 0 0 12px rgba(255, 255, 255, 0.3),
    inset 0 0 3px rgba(255, 255, 255, 0.5), 0 3px 3px rgba(0, 0, 0, 0.164);
  border-radius: 50%;
  transition: all 0.3s;
  height: 36px;
  width: 36px;
}

.iso-pro:hover span {
  opacity: 1;
}

.iso-pro:hover span:nth-child(1) {
  opacity: 0.2;
}

.iso-pro:hover span:nth-child(2) {
  opacity: 0.4;
  transform: translate(3px, -3px);
}

.iso-pro:hover span:nth-child(3) {
  opacity: 0.6;
  transform: translate(6px, -6px);
}
</style>
