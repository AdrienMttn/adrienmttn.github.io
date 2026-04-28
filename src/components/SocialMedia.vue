<script setup lang="ts">
import gsap from "gsap";
import { ref, type Ref, onMounted } from "vue";
const linkedin: Ref<HTMLAnchorElement | null> = ref(null);
const github: Ref<HTMLAnchorElement | null> = ref(null);

onMounted(() => {
  gsap.from(linkedin.value, {
    duration: 1,
    opacity: 0,
    x: 100,
    ease: "power2.out",
  });
  gsap.from(github.value, {
    duration: 1,
    opacity: 0,
    x: 100,
    delay: 0.5,
    ease: "power2.out",
  });
});
</script>

<template>
  <div
    class="z-10 h-screen w-30 fixed right-0 flex flex-col justify-center items-center"
  >
    <a
      ref="linkedin"
      href="https://www.linkedin.com/in/adrien-metton/"
      target="_blank"
      class="mb-4 cursor-pointer backdrop-blur-md rounded-full p-2"
    >
      <svg
        width="34"
        height="34"
        fill="none"
        role="img"
        aria-labelledby="title_logo_linekdin"
        aria-describedby="description_logo_linekdin"
        xmlns="http://www.w3.org/2000/svg"
      >
        <title id="title_logo_linekdin">LinkedIn logo</title>
        <desc id="description_logo_linekdin">
          Logotype representing the letters I and N
        </desc>
        <circle cx="17" cy="17" r="16.5" stroke="#000"></circle>
        <path
          d="M13.333 10.683c0 .943-.733 1.683-1.666 1.683-.934 0-1.667-.74-1.667-1.683C10 9.741 10.733 9 11.667 9c.933 0 1.666.74 1.666 1.683Zm0 3.03H10v10.77h3.333v-10.77Zm5.334 0h-3.334v10.77h3.334V18.83c0-3.164 4-3.434 4 0v5.655H26v-6.8c0-5.318-5.933-5.116-7.333-2.49v-1.482Z"
          fill="#000"
        ></path>
      </svg>
    </a>
    <a
      ref="github"
      href="https://github.com/adrienmttn"
      target="_blank"
      class="mb-4 cursor-pointer backdrop-blur-md rounded-full p-2"
    >
      <svg
        fill="#000000"
        width="34px"
        height="34px"
        viewBox="0 0 24 24"
        xmlns="http://www.w3.org/2000/svg"
        data-name="Github Logo"
      >
        <path
          d="M12,2.2467A10.00042,10.00042,0,0,0,8.83752,21.73419c.5.08752.6875-.21247.6875-.475,0-.23749-.01251-1.025-.01251-1.86249C7,19.85919,6.35,18.78423,6.15,18.22173A3.636,3.636,0,0,0,5.125,16.8092c-.35-.1875-.85-.65-.01251-.66248A2.00117,2.00117,0,0,1,6.65,17.17169a2.13742,2.13742,0,0,0,2.91248.825A2.10376,2.10376,0,0,1,10.2,16.65923c-2.225-.25-4.55-1.11254-4.55-4.9375a3.89187,3.89187,0,0,1,1.025-2.6875,3.59373,3.59373,0,0,1,.1-2.65s.83747-.26251,2.75,1.025a9.42747,9.42747,0,0,1,5,0c1.91248-1.3,2.75-1.025,2.75-1.025a3.59323,3.59323,0,0,1,.1,2.65,3.869,3.869,0,0,1,1.025,2.6875c0,3.83747-2.33752,4.6875-4.5625,4.9375a2.36814,2.36814,0,0,1,.675,1.85c0,1.33752-.01251,2.41248-.01251,2.75,0,.26251.1875.575.6875.475A10.0053,10.0053,0,0,0,12,2.2467Z"
        />
      </svg>
    </a>
  </div>
</template>
