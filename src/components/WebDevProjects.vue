<script setup lang="ts">
import { ref, onMounted } from "vue";
import { useThemeStore } from "../store/theme";

const themeStore = useThemeStore();

// Import project images directly
import isepImage from "../assets/images/WebDevProjects/ISEP.png";
import hspImage from "../assets/images/WebDevProjects/HSP.png";
import sympyImage from "../assets/images/WebDevProjects/sympy.png";
import gsocImage from "../assets/images/WebDevProjects/gsoc.png";

// Function to get technology-specific colors
const getTechColor = (techName: string) => {
  const colors = {
    // Frontend
    HTML5: "bg-orange-500",
    CSS3: "bg-blue-500",
    JavaScript: "bg-yellow-500",
    "Vue.js": "bg-green-500",
    TypeScript: "bg-blue-600",

    // Backend
    Python: "bg-yellow-600",
    Flask: "bg-gray-700",
    Django: "bg-green-700",
    "Node.js": "bg-green-600",

    // Databases
    SQLite: "bg-blue-400",
    MongoDB: "bg-green-600",
    MySQL: "bg-blue-600",
    Redis: "bg-red-500",

    // Tools & Libraries
    Git: "bg-orange-600",
    GitHub: "bg-gray-800",
    Docker: "bg-blue-500",
    SymPy: "bg-green-500",
    Codecov: "bg-pink-500",
    Celery: "bg-green-400",

    // Machine Learning
    TensorFlow: "bg-orange-500",
    PyTorch: "bg-red-600",
    NumPy: "bg-blue-500",
    Pandas: "bg-purple-600",

    // Default
    default: "bg-indigo-500",
  };

  return colors[techName] || colors["default"];
};

// Add direct references to image paths for better reliability
const projectImagePaths = {
  isep: isepImage,
  hsp: hspImage,
  sympy: sympyImage,
  gsoc: gsocImage,
};

const projects = ref([
  {
    id: 3,
    title: "Google Summer of Code at SymPy",
    description:
      "Implementing a formal power series domain system for SymPy to enhance its symbolic mathematics capabilities, with expected completion in Summer 2025.",
    image: sympyImage,
    upcoming: true,
    technologies: [
      { name: "Python", img: "Python.png" },
      { name: "SymPy", img: "SymPy.png" },
      { name: "Codecov", img: "Codecov.png" },
    ],
    links: [
      {
        type: "github",
        url: "https://github.com/sympy/sympy/pulls?q=author%3AJatinbhardwaj-093",
        icon: "bi bi-github",
      },
      {
        type: "rss",
        url: "https://planet.sympy.org",
        icon: "bi bi-rss",
      },
    ],
    features: [
      "Enhancing ring_series module with PowerSeriesRing domain system",
      "Implementing efficient series expansions over diverse coefficient domains (QQ, RR)",
      "Developing Taylor expansions for common functions (sin, exp)",
      "Creating comprehensive documentation and improving performance",
    ],
  },
  {
    id: 1,
    title: "Influencer-Sponsor Engagement Platform",
    description:
      "A comprehensive collaboration platform connecting influencers with sponsors and sponsorship opportunities.",
    image: isepImage,
    technologies: [
      { name: "HTML5", img: "HTML5.png" },
      { name: "CSS3", img: "CSS3.png" },
      { name: "JavaScript", img: "JavaScript.png" },
      { name: "Flask", img: "Flask.png" },
      { name: "SQLite", img: "SQLite.png" },
    ],
    links: [
      {
        type: "github",
        url: "https://github.com/Jatinbhardwaj-093/Infulencer-Sponsor-Engagement-Platform",
        icon: "bi bi-github",
      },
      {
        type: "docs",
        url: "https://drive.google.com/drive/folders/1SLRgwuTLKnKVfdY9br0idI0x_NHyb0Qn?usp=drive_link",
        icon: "bi bi-file-earmark-text",
      },
    ],
    features: [
      "Profile matching for influencers and sponsors",
      "Detailed analytics dashboard",
      "Secure messaging system",
      "Contract management tools",
    ],
  },
  {
    id: 2,
    title: "HouseHold Service Platform",
    description:
      "A booking service platform that helps users find and schedule household services with verified service providers.",
    image: hspImage,
    technologies: [
      { name: "Vue.js", img: "Vue.js.png" },
      { name: "Flask", img: "Flask.png" },
      { name: "SQLite", img: "SQLite.png" },
      { name: "Redis", img: "Redis.png" },
      { name: "Celery", img: "Celery.png" },
    ],
    links: [
      {
        type: "github",
        url: "https://github.com/Jatinbhardwaj-093/HouseHold-Service-Platform",
        icon: "bi bi-github",
      },
      {
        type: "docs",
        url: "https://drive.google.com/drive/folders/1YR5UsPf4jtXYstgQJDPUFEjy33uew83I?usp=drive_link",
        icon: "bi bi-file-earmark-text",
      },
      {
        type: "figma",
        url: "https://www.figma.com/design/a5MomTlXdFQ1qz7lAzog7E/Househod-Service-MAD-1?node-id=0-1&t=Xo1ho1DEgCnSpn03-1",
        icon: "bi bi-figma",
      },
    ],
    features: [
      "Real-time service provider tracking",
      "Secure payment processing",
      "Rating and review system",
      "Service provider verification process",
    ],
  },
]);

const activeTab = ref("all");

// Improved error handling for images
const handleImageError = (e: Event, projectId: number) => {
  const target = e.target as HTMLImageElement;
  console.error(`Image failed to load for project ${projectId}`);
  if (target) {
    // Instead of hiding, set a fallback background color
    target.style.backgroundColor = "#1f1f1f";
    // Try reloading the image with a different approach
    if (projectId === 1) {
      target.src = projectImagePaths.isep;
    } else if (projectId === 2) {
      target.src = projectImagePaths.hsp;
    } else if (projectId === 3) {
      target.src = projectImagePaths.sympy;
    }
  }
};
</script>

<template>
  <section class="py-10">
    <div class="container mx-auto px-4">
      <div class="mb-10 text-center">
        <h2
          class="text-3xl font-bold mb-2"
          :class="{
            'text-white': themeStore.theme === 'dark',
            'text-black': themeStore.theme === 'light',
          }"
        >
          Featured Projects
        </h2>
        <div class="h-1 w-24 bg-indigo-600 mx-auto rounded-full"></div>
        <p
          class="mt-4 max-w-2xl mx-auto"
          :class="{
            'text-gray-300': themeStore.theme === 'dark',
            'text-gray-600': themeStore.theme === 'light',
          }"
        >
          Discover my portfolio of innovative projects, from open source
          contributions to full-stack applications, where clean code meets
          creative design.
        </p>
      </div>

      <div
        class="grid grid-cols-1 lg:grid-cols-2 gap-8 mb-8 projects-container"
      >
        <div
          v-for="(project, index) in projects"
          :key="project.id"
          class="project-card rounded-xl overflow-hidden shadow-lg transition-all duration-500 hover:shadow-2xl border"
          :class="{
            'transform-gpu hover:-translate-y-2': index % 2 === 0,
            'transform-gpu hover:translate-y-2': index % 2 !== 0,
            'bg-gray-800/60 border-gray-700': themeStore.theme === 'dark',
            'bg-white border-gray-100': themeStore.theme === 'light',
          }"
        >
          <!-- Image -->
          <div class="relative overflow-hidden group min-h-[160px]">
            <template v-if="project.id === 3">
              <div
                class="flex items-center justify-center w-full min-h-[160px] h-64 px-0 gsoc-sympy-container"
              >
                <img
                  :src="gsocImage"
                  alt="GSoC logo"
                  class="w-1/2 h-full object-contain p-0 pr-1 transition-transform duration-700 group-hover:scale-105 gsoc-logo"
                  loading="eager"
                />
                <img
                  :src="sympyImage"
                  alt="SymPy logo"
                  class="w-1/2 h-full object-contain p-0 pl-1 transition-transform duration-700 group-hover:scale-105 sympy-logo"
                  loading="eager"
                  @error="handleImageError($event, project.id)"
                />
              </div>
            </template>
            <template v-else>
              <img
                :src="project.image"
                :alt="`${project.title} screenshot`"
                class="w-full min-h-[160px] h-64 object-cover object-top transition-transform duration-700 group-hover:scale-105"
                loading="eager"
                @error="handleImageError($event, project.id)"
              />
            </template>
            <div
              class="absolute inset-0 bg-gradient-to-t from-black/70 via-black/20 to-transparent opacity-60 group-hover:opacity-80 transition-opacity duration-300"
            ></div>

            <!-- Project title overlay -->
            <div class="absolute inset-0 flex items-end p-4 sm:p-6">
              <h3
                class="text-lg sm:text-xl md:text-2xl font-bold text-white project-title"
              >
                {{ project.title }}
              </h3>
              <div
                v-if="project.upcoming"
                class="absolute top-4 right-4 bg-indigo-600 text-white text-xs font-bold px-2 py-1 rounded-md shadow-md transform transition-transform duration-300 hover:scale-105"
              >
                Upcoming
              </div>
            </div>
          </div>

          <!-- Content -->
          <div class="p-5 space-y-3">
            <p
              :class="{
                'text-gray-300': themeStore.theme === 'dark',
                'text-gray-700': themeStore.theme === 'light',
              }"
            >
              {{ project.description }}
            </p>

            <!-- Features -->
            <div class="space-y-2">
              <h4
                class="font-semibold"
                :class="{
                  'text-white': themeStore.theme === 'dark',
                  'text-black': themeStore.theme === 'light',
                }"
              >
                Key Features:
              </h4>
              <ul class="list-disc pl-5 space-y-1">
                <li
                  v-for="(feature, i) in project.features"
                  :key="i"
                  class="text-sm"
                  :class="{
                    'text-gray-300': themeStore.theme === 'dark',
                    'text-gray-700': themeStore.theme === 'light',
                  }"
                >
                  {{ feature }}
                </li>
              </ul>
            </div>

            <!-- Technologies -->
            <div class="mt-3">
              <h4
                class="font-semibold mb-2"
                :class="{
                  'text-white': themeStore.theme === 'dark',
                  'text-black': themeStore.theme === 'light',
                }"
              >
                Technologies Used:
              </h4>
              <div class="flex flex-wrap gap-1.5 tags-container">
                <div
                  v-for="(tech, i) in project.technologies"
                  :key="i"
                  class="tech-badge group flex items-center gap-1.5 px-2 py-1 rounded-sm"
                  :class="{
                    'bg-gray-700/70 border border-gray-600':
                      themeStore.theme === 'dark',
                    'bg-gray-100 border border-gray-200':
                      themeStore.theme === 'light',
                  }"
                >
                  <div
                    class="w-2 h-2 rounded-full flex-shrink-0"
                    :class="getTechColor(tech.name)"
                  ></div>
                  <span
                    class="text-xs font-medium"
                    :class="{
                      'text-gray-300': themeStore.theme === 'dark',
                      'text-gray-700': themeStore.theme === 'light',
                    }"
                    >{{ tech.name }}</span
                  >
                </div>
              </div>
            </div>

            <!-- Links -->
            <div
              class="pt-3 mt-3 border-t flex justify-between items-center"
              :class="{
                'border-gray-700': themeStore.theme === 'dark',
                'border-gray-100': themeStore.theme === 'light',
              }"
            >
              <div class="flex space-x-3">
                <a
                  v-for="(link, i) in project.links"
                  :key="i"
                  :href="link.url"
                  target="_blank"
                  rel="noopener noreferrer"
                  class="link-button p-2 rounded-full transition-colors duration-300"
                  :class="{
                    'text-gray-400 hover:text-indigo-400':
                      themeStore.theme === 'dark',
                    'text-gray-600 hover:text-indigo-600':
                      themeStore.theme === 'light',
                  }"
                  :aria-label="`Link to ${link.type} for ${project.title}`"
                >
                  <i :class="link.icon" class="text-lg"></i>
                </a>
              </div>

              <a
                :href="project.links[0].url"
                target="_blank"
                rel="noopener noreferrer"
                class="inline-flex items-center text-sm font-semibold text-indigo-600 dark:text-indigo-400 hover:text-indigo-800 dark:hover:text-indigo-300 btn-view-project"
              >
                <span class="relative">
                  View Project
                  <!-- Animation is handled by CSS in .btn-view-project span.relative::after -->
                </span>
                <svg
                  xmlns="http://www.w3.org/2000/svg"
                  class="ml-1 h-4 w-4 transition-transform duration-300"
                  fill="none"
                  viewBox="0 0 24 24"
                  stroke="currentColor"
                >
                  <path
                    stroke-linecap="round"
                    stroke-linejoin="round"
                    stroke-width="2"
                    d="M9 5l7 7-7 7"
                  />
                </svg>
              </a>
            </div>
          </div>
        </div>
      </div>

      <!-- More Projects Button -->
      <div class="mt-8 text-center">
        <a
          href="https://github.com/Jatinbhardwaj-093"
          target="_blank"
          rel="noopener noreferrer"
          class="inline-flex items-center justify-center px-6 py-3 border border-transparent text-base font-medium rounded-md shadow-sm text-white bg-indigo-600 hover:bg-indigo-700 transition-colors duration-300"
        >
          <i class="bi bi-github mr-2"></i>
          View More on GitHub
        </a>
      </div>
    </div>
  </section>
</template>

<style scoped>
.projects-container {
  perspective: 1000px;
}

.project-card {
  position: relative;
  transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
  transform-style: preserve-3d;
  transform: translateZ(0);
  background: var(--card-bg, #ffffff);
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.05);
  animation: projectCardEntrance 0.8s cubic-bezier(0.25, 1, 0.5, 1) backwards;
}

.project-card:nth-child(1) {
  animation-delay: 0.2s;
}
.project-card:nth-child(2) {
  animation-delay: 0.4s;
}
.project-card:nth-child(3) {
  animation-delay: 0.6s;
}
.project-card:nth-child(4) {
  animation-delay: 0.8s;
}

@keyframes projectCardEntrance {
  0% {
    opacity: 0;
    transform: translateY(60px) translateZ(-30px) rotateX(-10deg);
  }
  100% {
    opacity: 1;
    transform: translateY(0) translateZ(0) rotateX(0);
  }
}

.project-card:hover {
  transform: translateY(-12px) translateZ(10px) scale(1.01);
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.1),
    0 10px 10px -5px rgba(0, 0, 0, 0.04);
}

.project-card img {
  transition: all 0.6s cubic-bezier(0.16, 1, 0.3, 1);
  transform: scale(1);
  filter: brightness(1) saturate(1);
}

.project-card:hover img {
  transform: scale(1.05);
  filter: brightness(1.1) saturate(1.1);
}

.project-title {
  position: relative;
  transition: all 0.4s cubic-bezier(0.16, 1, 0.3, 1);
  overflow: hidden;
}

.project-title::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 0%;
  height: 2px;
  background: white; /* White underline */
  transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
}

.project-card:hover .project-title::after {
  width: 100%;
}

.project-card:hover .project-title {
  /* Remove gradient color change effect and text-shadow */
  color: white; /* Keep text white */
  /* Keep the underline effect only */
  filter: drop-shadow(
    0 1px 2px rgba(0, 0, 0, 0.3)
  ); /* Light shadow for depth */
}

.tags-container span {
  position: relative;
  overflow: hidden;
  transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
  transform: translateZ(0);
  animation: tagEntrance 0.6s cubic-bezier(0.16, 1, 0.3, 1) backwards;
}

.tags-container span:nth-child(1) {
  animation-delay: 0.8s;
}
.tags-container span:nth-child(2) {
  animation-delay: 0.9s;
}
.tags-container span:nth-child(3) {
  animation-delay: 1s;
}
.tags-container span:nth-child(4) {
  animation-delay: 1.1s;
}
.tags-container span:nth-child(5) {
  animation-delay: 1.2s;
}

@keyframes tagEntrance {
  0% {
    opacity: 0;
    transform: translateY(10px) scale(0.8);
  }
  100% {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

.project-card:hover .tags-container span {
  transform: translateY(-2px);
  box-shadow: 0 4px 8px -2px rgba(79, 70, 229, 0.2);
}

.btn-view-project {
  position: relative;
  overflow: hidden;
  transition: all 0.5s cubic-bezier(0.16, 1, 0.3, 1);
  transform: translateZ(0);
  z-index: 1;
  padding: 0.25rem 0.5rem;
  border-radius: 0.25rem;
}

.btn-view-project::before {
  content: "";
  position: absolute;
  top: 0;
  left: 0;
  width: 100%;
  height: 100%;
  /* Background gradient removed */
  opacity: 0;
  z-index: -1;
  transition: opacity 0.5s cubic-bezier(0.16, 1, 0.3, 1);
}

.btn-view-project:hover,
.project-card:hover .btn-view-project {
  /* Keeping text color as is instead of forcing white */
  transform: translateY(-2px);
  box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1),
    0 4px 6px -2px rgba(0, 0, 0, 0.05);
}

.btn-view-project:hover::before,
.project-card:hover .btn-view-project::before {
  /* Preventing background effect from showing */
  opacity: 0;
}

.btn-view-project svg {
  transition: transform 0.4s cubic-bezier(0.16, 1, 0.3, 1);
}

.btn-view-project:hover svg,
.project-card:hover .btn-view-project svg {
  transform: translateX(4px);
}

/* Dark mode specific adjustments */
:root[data-theme="dark"] .project-card {
  --card-bg: #1f2937;
  box-shadow: 0 5px 15px rgba(0, 0, 0, 0.2);
}

:root[data-theme="dark"] .project-card:hover {
  box-shadow: 0 20px 25px -5px rgba(0, 0, 0, 0.3),
    0 10px 10px -5px rgba(0, 0, 0, 0.2);
}

:root[data-theme="dark"] .project-title {
  --title-hover: #818cf8;
}

:root[data-theme="dark"] .tags-container span {
  --tag-bg-hover: #3730a3;
  --tag-color-hover: #e0e7ff;
}

/* Loading state animation */
.loading-skeleton {
  position: relative;
  overflow: hidden;
  background: #e2e8f0;
  animation: skeletonPulse 1.5s ease-in-out infinite;
}

:root[data-theme="dark"] .loading-skeleton {
  background: #374151;
}

.loading-skeleton::after {
  content: "";
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  transform: translateX(-100%);
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.2) 20%,
    rgba(255, 255, 255, 0.5) 60%,
    rgba(255, 255, 255, 0)
  );
  animation: shimmer 2s infinite;
}

:root[data-theme="dark"] .loading-skeleton::after {
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.1) 20%,
    rgba(255, 255, 255, 0.2) 60%,
    rgba(255, 255, 255, 0)
  );
}

@keyframes shimmer {
  100% {
    transform: translateX(100%);
  }
}

@keyframes skeletonPulse {
  0%,
  100% {
    opacity: 1;
  }
  50% {
    opacity: 0.7;
  }
}

/* Responsive animations */
@media (max-width: 768px) {
  .project-card {
    animation-delay: calc(0.15s * var(--index, 0));
  }

  .project-card:hover {
    transform: translateY(-8px) translateZ(5px);
  }
}

/* Image hover effect with parallax and shine effect */
.project-card .relative {
  overflow: hidden;
}

.project-card:hover img {
  transform: scale(1.07);
}

.project-card .relative::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 50%;
  height: 100%;
  background: linear-gradient(
    to right,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.3) 100%
  );
  transform: skewX(-25deg);
  z-index: 2;
  transition: all 0.75s;
  opacity: 0;
}

.project-card:hover .relative::before {
  animation: shine 1.5s cubic-bezier(0.25, 1, 0.5, 1);
}

@keyframes shine {
  0% {
    left: -100%;
    opacity: 0;
  }
  50% {
    opacity: 0.6;
  }
  100% {
    left: 150%;
    opacity: 0;
  }
}

/* Technology badges with pop effect */
.tech-badge {
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
  animation: fadeIn 0.5s ease-out both;
  animation-delay: calc(var(--badge-index, 0) * 100ms + 800ms);
  border: 1px solid transparent;
}

.tech-badge:hover {
  transform: translateY(-3px) scale(1.05);
  box-shadow: 0 4px 8px -4px rgba(0, 0, 0, 0.1);
}

/* Improve tech icon container sizing */
.tech-badge .w-5 {
  display: flex;
  align-items: center;
  justify-content: center;
  margin-right: 0.25rem;
}

@keyframes fadeIn {
  from {
    opacity: 0;
    transform: translateY(10px) scale(0.9);
  }
  to {
    opacity: 1;
    transform: translateY(0) scale(1);
  }
}

/* Enhanced link button effects */
.link-button {
  position: relative;
  overflow: hidden;
  transition: all 0.4s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.link-button:hover {
  transform: translateY(-3px);
  /* No background color change on hover */
}

.link-button:active {
  transform: translateY(0) scale(0.95);
}

/* View Project link animation - span underline effect */
.btn-view-project span.relative {
  position: relative;
  display: inline-block;
  overflow: hidden;
  padding-bottom: 2px;
}

.btn-view-project span.relative::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: currentColor;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
}

.btn-view-project:hover svg,
.project-card:hover .btn-view-project svg {
  transform: translateX(5px);
}

/* More Projects Button animation */
.mt-8 a {
  position: relative;
  overflow: hidden;
  transition: all 0.5s cubic-bezier(0.34, 1.56, 0.64, 1);
}

.mt-8 a::before {
  content: "";
  position: absolute;
  top: 0;
  left: -100%;
  width: 100%;
  height: 100%;
  background: linear-gradient(
    90deg,
    rgba(255, 255, 255, 0) 0%,
    rgba(255, 255, 255, 0.2) 50%,
    rgba(255, 255, 255, 0) 100%
  );
  transition: all 0.5s cubic-bezier(0.25, 1, 0.5, 1);
}

.mt-8 a:hover {
  transform: translateY(-5px);
  box-shadow: 0 10px 25px -10px rgba(99, 102, 241, 0.6);
}

.mt-8 a:hover::before {
  animation: buttonShine 1.5s infinite;
}

@keyframes buttonShine {
  0% {
    left: -100%;
    opacity: 0;
  }
  50% {
    opacity: 1;
  }
  100% {
    left: 100%;
    opacity: 0;
  }
}

.mt-8 a:active {
  transform: translateY(0) scale(0.98);
}

/* Section title animation */
h2.text-3xl {
  position: relative;
  display: inline-block;
  animation: titleFadeIn 1s cubic-bezier(0.16, 1, 0.3, 1) both;
}

@keyframes titleFadeIn {
  0% {
    opacity: 0;
    transform: translateY(-20px);
  }
  100% {
    opacity: 1;
    transform: translateY(0);
  }
}

.h-1.w-24 {
  animation: lineExpand 1.2s cubic-bezier(0.34, 1.56, 0.64, 1) both;
  transform-origin: center;
}

@keyframes lineExpand {
  0% {
    transform: scaleX(0);
    opacity: 0;
  }
  100% {
    transform: scaleX(1);
    opacity: 1;
  }
}

/* Ensure images display correctly on mobile */
@media (max-width: 640px) {
  .project-card img {
    display: block !important; /* Force display in case error handler hides it */
    min-height: 160px;
    max-height: 200px;
    width: 100%;
    object-position: center top;
  }

  .project-card .relative {
    background-color: #1f1f1f; /* Fallback background if image fails */
  }

  /* GSoC and SymPy image container adjustment for small screens */
  .gsoc-sympy-container {
    min-height: 90px !important;
    height: 120px !important;
    padding: 0.5rem 0;
  }

  .gsoc-sympy-container img {
    object-fit: contain !important;
    max-height: 80px !important;
  }

  .gsoc-logo {
    width: 35% !important;
    max-width: 35% !important;
  }

  .sympy-logo {
    width: 30% !important;
    max-width: 30% !important;
  }

  /* Optimize for very small screens */
  @media (max-width: 375px) {
    .gsoc-sympy-container {
      min-height: 80px !important;
      height: 100px !important;
    }

    .gsoc-sympy-container img {
      max-height: 60px !important;
    }

    .gsoc-logo {
      width: 30% !important;
      max-width: 30% !important;
    }

    .sympy-logo {
      width: 25% !important;
      max-width: 25% !important;
    }
  }
}

/* Base image styling enhancements */
.project-card img {
  max-width: 100%;
  object-fit: cover;
  backface-visibility: hidden; /* Prevents glitches during animation */
  will-change: transform; /* Optimizes for animation */
}

/* Button animation styles */
.btn-view-project span.relative::after {
  content: "";
  position: absolute;
  bottom: 0;
  left: 0;
  width: 100%;
  height: 2px;
  background: currentColor;
  transform: scaleX(0);
  transform-origin: left;
  transition: transform 0.4s cubic-bezier(0.25, 1, 0.5, 1);
}

.project-card:hover .btn-view-project span.relative::after,
.btn-view-project:hover span.relative::after {
  transform: scaleX(1);
  transition-delay: 0.1s;
}

/* Ensure mobile view gets the same animation experience as desktop */
@media (max-width: 640px) {
  .project-card:hover .btn-view-project {
    /* Keeping text color as is instead of forcing white */
    transform: translateY(-2px);
  }

  .project-card:hover .btn-view-project::before {
    /* Preventing background effect from showing */
    opacity: 0;
  }
}
</style>
