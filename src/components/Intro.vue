<script setup lang="ts">
import { ref, Ref } from 'vue';
import ContactLink from './ContactLink.vue';

interface MyData {
  firstName: string;
  lastName: string;
}

const myData: Ref<MyData> = ref({
  firstName: 'Jatin',
  lastName: 'Bhardwaj'
});

</script>

<template>
  <div class=" absolute block lg:hidden top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2">
    <p class="text-3xl text-black font-bold dark:text-white">Hi,</p>
    <div>
      <span class="text-3xl text-black font-bold dark:text-white">
        I'm {{ myData.firstName }}
      </span>
      <span class="text-3xl text-purple-600 font-bold ml-1 dark:text-purple-500">
        {{ myData.lastName }}
      </span>
    </div>
    <div class="mt-2">
      <span class="text-xl text-red-700 dark:text-red-500">
        Web Developer, Data Scientist
      </span>
    </div>
    <div class="flex items-center justify-start  ml-4 space-x-6">
      <div class="bg-purple-600 text-white px-4 py-2 rounded-xl mt-8
                    shadow-lg shadow-black flex items-center justify-center
                    hover:transform hover:transform-ease-in-out hover:scale-105 
                    cursor-pointer" @click="$router.push('/about')">
        <i class="bi bi-person-lines-fill text-lg mr-2"></i>
        <p class="font-bold text-m text-white">More About Me</p>
      </div>
      <div class="bg-purple-600 text-white px-8 py-2 rounded-xl mt-8
                    shadow-lg shadow-black flex items-center justify-center
                    hover:transform hover:transform-ease-in-out hover:scale-105 
                    cursor-pointer" @click="$router.push('/contact')">
        <i class="bi bi-envelope-at-fill text-lg mr-2"></i>
        <p class="font-bold text-m text-white">Contact Me</p>
      </div>
    </div>
    <div class="mt-16 w-min mx-auto">
      <ContactLink />
    </div>
  </div>

  <div class="hidden lg:block">
    <p class="absolute top-1/4 left-0 transform rotate-90 text-3xl text-purple-500 font-bold font-ubuntu">
  Jatin Bhardwaj
</p>
    <img src="../assets/images/profileImage/myimage.png" alt="" class="absolute top-1/2 left-1/2 transform -translate-x-[45%] -translate-y-1/3 z-10 h-[600px] ">
    <!-- Main Circle Container -->
    <div
      class="rounded-full bg-purple-600 shadow-lg shadow-black h-[500px] w-[500px] absolute top-1/2 left-1/2 transform -translate-x-1/2 -translate-y-1/2 z-0">

      <!-- Orbit Rings -->
      <div class="orbit-ring ring-1">
        <img src="../assets/images/C.png" alt="C Logo" class="tech-icon">
        <img src="../assets/images/C++.png" alt="C++ Logo" class="tech-icon">
        <img src="../assets/images/Python.png" alt="Python Logo" class="tech-icon">
        <img src="../assets/images/JavaScript.png" alt="JavaScript Logo" class="tech-icon">
        <img src="../assets/images/HTML5.png" alt="HTML5 Logo" class="tech-icon">
        <img src="../assets/images/CSS3.png" alt="CSS3 Logo" class="tech-icon">
      </div>

      <div class="orbit-ring ring-2">
        <img src="../assets/images/Vue.js.png" alt="Vue Logo" class="tech-icon">
        <img src="../assets/images/Flask.png" alt="Flask Logo" class="tech-icon">
        <img src="../assets/images/SQLite.png" alt="SQLite Logo" class="tech-icon">
        <img src="../assets/images/PyTorch.png" alt="PyTorch Logo" class="tech-icon">
        <img src="../assets/images/TensorFlow.png" alt="TensorFlow Logo" class="tech-icon">
        <img src="../assets/images/NumPy.png" alt="NumPy Logo" class="tech-icon">
        <img src="../assets/images/Django.png" alt="Django Logo" class="tech-icon">
        <img src="../assets/images/Docker.png" alt="Docker Logo" class="tech-icon">
      </div>

      <div class="orbit-ring ring-3">
        <img src="../assets/images/Pandas.png" alt="Pandas Logo" class="tech-icon">
        <img src="../assets/images/Redis.png" alt="Redis Logo" class="tech-icon">
        <img src="../assets/images/Celery.png" alt="Celery Logo" class="tech-icon">
        <img src="../assets/images/Git.png" alt="Git Logo" class="tech-icon">
        <img src="../assets/images/GitHub.png" alt="GitHub Logo" class="tech-icon">
        <img src="../assets/images/Postman.png" alt="Postman Logo" class="tech-icon">
        <img src="../assets/images/Kubernetes.png" alt="Kubernetes Logo" class="tech-icon">
        <img src="../assets/images/GraphQL.png" alt="Graphql Logo" class="tech-icon">
        <img src="../assets/images/TypeScript.png" alt="TypeScript Logo" class="tech-icon">
        <img src="../assets/images/MongoDB.png" alt="MongoDB Logo" class="tech-icon">
      </div>
      </div>

      <div class="absolute bottom-0 right-0 flex flex-col items-center gap-y-4 p-4">

        <a href="https://www.linkedin.com/in/jatin-bhardwaj-b5962921a/" class="group relative">
          <i class="bi bi-linkedin text-2xl text-gray-600 group-hover:text-purple-600 
            hover:transform hover:scale-110 hover:duration-300 hover:transition-ease-in-out
              cursor-pointer">
                <span class="absolute opacity-0 group-hover:opacity-100 text-purple-600 text-sm font-semibold
                    transition-opacity duration-300 top-2 right-8">
                    LinkedIn
                </span>
              </i>
        </a>

        <a href="https://github.com/Jatinbhardwaj-093" class="group relative">
          <i class="bi bi-github text-2xl text-gray-600 group-hover:text-purple-600 
            hover:transform hover:scale-110 hover:duration-300 hover:transition-ease-in-out
              cursor-pointer">
                <span class="absolute opacity-0 group-hover:opacity-100 text-purple-600 text-sm font-semibold
                    transition-opacity duration-300 top-2 right-8">
                    Github
                </span>
              </i>
        </a>
        <a href="https://x.com/Jatin0932" class="group relative">
          <i class="bi bi-twitter-x text-2xl text-gray-600 group-hover:text-purple-600 
            hover:transform hover:scale-110 hover:duration-300 hover:transition-ease-in-out
              cursor-pointer">
                <span class="absolute opacity-0 group-hover:opacity-100 text-purple-600 text-sm font-semibold
                    transition-opacity duration-300 top-2 right-8">
                    X
                </span>
              </i>
        </a>
        <a href="javascript:void(0)" onclick="window.open('https://mail.google.com/mail/?view=cm&fs=1&to=bhardwajjatin093@gmail.com&su=Hello&body=I wanted to ask...');" class="group relative">
              <svg
                fill="#4b5563"
                viewBox="0 0 24 24"
                role="img"
                xmlns="http://www.w3.org/2000/svg"
                class="w-6 h-6  text-gray-600 group-hover:fill-purple-600 
            hover:transform hover:scale-110 hover:duration-300 hover:transition-ease-in-out
              cursor-pointer"
                >
                <path
                    d="M24 5.457v13.909c0 .904-.732 1.636-1.636 1.636h-3.819V11.73L12 16.64l-6.545-4.91v9.273H1.636A1.636 1.636 0 0 1 0 19.366V5.457c0-2.023 2.309-3.178 3.927-1.964L5.455 4.64 12 9.548l6.545-4.91 1.528-1.145C21.69 2.28 24 3.434 24 5.457z"
                ></path>
                </svg>
                <span class="absolute opacity-0 group-hover:opacity-100 text-purple-600 text-sm font-semibold
                    transition-opacity duration-300 top-2 right-8">
                    GMail
                </span>
        </a>
    </div>
  </div>
</template>

<style scoped>
.orbit-ring {
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  border-radius: 50%;
  z-index: 1;
  display: flex;
  justify-content: center;
  align-items: center;
  box-shadow: none !important;

}

.tech-icon {
  position: absolute;
  width: 32px;
  height: 32px;
  transform-origin: center;
  transition: transform 1s;
  z-index: 2;
}

/* Adjust container to prevent scrolling */
.hidden.lg\:block {
  position: relative;
  width: 100%;
  height: 88vh;
  overflow: hidden;
}

.ring-1 {
  width: 440px;
  height: 440px;
  animation: spin 270s linear infinite;
}

.ring-2 {
  width: 560px;
  height: 560px;
  animation: spin 270s linear infinite;
}

.ring-3 {
  width: 680px;
  height: 680px;
  animation: spin 270s linear infinite;
}

/* Position icons in first ring */
.ring-1 .tech-icon:nth-child(1) {
  transform: translate(-50%, -50%) rotate(0deg) translateY(-320px) rotate(0deg);
}

.ring-1 .tech-icon:nth-child(2) {
  transform: translate(-50%, -50%) rotate(60deg) translateY(-320px) rotate(-60deg);
}

.ring-1 .tech-icon:nth-child(3) {
  transform: translate(-50%, -50%) rotate(120deg) translateY(-320px) rotate(-120deg);
}

.ring-1 .tech-icon:nth-child(4) {
  transform: translate(-50%, -50%) rotate(180deg) translateY(-320px) rotate(-180deg);
}

.ring-1 .tech-icon:nth-child(5) {
  transform: translate(-50%, -50%) rotate(240deg) translateY(-320px) rotate(-240deg);
}

.ring-1 .tech-icon:nth-child(6) {
  transform: translate(-50%, -50%) rotate(300deg) translateY(-320px) rotate(-300deg);
}

/* Position icons in second ring */
.ring-2 .tech-icon:nth-child(1) {
  transform: translate(-50%, -50%) rotate(0deg) translateY(-380px) rotate(0deg);
}

.ring-2 .tech-icon:nth-child(2) {
  transform: translate(-50%, -50%) rotate(45deg) translateY(-380px) rotate(-45deg);
}

.ring-2 .tech-icon:nth-child(3) {
  transform: translate(-50%, -50%) rotate(90deg) translateY(-380px) rotate(-90deg);
}

.ring-2 .tech-icon:nth-child(4) {
  transform: translate(-50%, -50%) rotate(135deg) translateY(-380px) rotate(-135deg);
}

.ring-2 .tech-icon:nth-child(5) {
  transform: translate(-50%, -50%) rotate(180deg) translateY(-380px) rotate(-180deg);
}

.ring-2 .tech-icon:nth-child(6) {
  transform: translate(-50%, -50%) rotate(225deg) translateY(-380px) rotate(-225deg);
}

.ring-2 .tech-icon:nth-child(7) {
  transform: translate(-50%, -50%) rotate(270deg) translateY(-380px) rotate(-270deg);
}

.ring-2 .tech-icon:nth-child(8) {
  transform: translate(-50%, -50%) rotate(315deg) translateY(-380px) rotate(-315deg);
}

/* Position icons in third ring */
.ring-3 .tech-icon:nth-child(1) {
  transform: translate(-50%, -50%) rotate(0deg) translateY(-480px) rotate(0deg);
}

.ring-3 .tech-icon:nth-child(2) {
  transform: translate(-50%, -50%) rotate(36deg) translateY(-480px) rotate(-36deg);
}

.ring-3 .tech-icon:nth-child(3) {
  transform: translate(-50%, -50%) rotate(72deg) translateY(-480px) rotate(-72deg);
}

.ring-3 .tech-icon:nth-child(4) {
  transform: translate(-50%, -50%) rotate(108deg) translateY(-480px) rotate(-108deg);
}

.ring-3 .tech-icon:nth-child(5) {
  transform: translate(-50%, -50%) rotate(144deg) translateY(-480px) rotate(-144deg);
}

.ring-3 .tech-icon:nth-child(6) {
  transform: translate(-50%, -50%) rotate(180deg) translateY(-480px) rotate(-180deg);
}

.ring-3 .tech-icon:nth-child(7) {
  transform: translate(-50%, -50%) rotate(216deg) translateY(-480px) rotate(-216deg);
}

.ring-3 .tech-icon:nth-child(8) {
  transform: translate(-50%, -50%) rotate(252deg) translateY(-480px) rotate(-252deg);
}

.ring-3 .tech-icon:nth-child(9) {
  transform: translate(-50%, -50%) rotate(288deg) translateY(-480px) rotate(-288deg);
}

.ring-3 .tech-icon:nth-child(10) {
  transform: translate(-50%, -50%) rotate(324deg) translateY(-480px) rotate(-324deg);
}

/* Keyframe for orbit rotation */
@keyframes spin {
  from {
    transform: translate(-50%, -50%) rotate(0deg);
  }

  to {
    transform: translate(-50%, -50%) rotate(360deg);
  }
}


.hidden {
  visibility: hidden;
}

@media (min-width: 1024px) {
  .hidden {
    visibility: visible;
  }
}
</style>
