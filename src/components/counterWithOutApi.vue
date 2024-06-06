<template>
  <section
    ref="elementToWatch"
    id="ele"
    class="bgchoose bg-sky-50 sm:w-full w-[90%] mx-auto border-2 text-blue-900 border-white shadow-2xl rounded-3xl my-10 px-12 py-5 sm:flex justify-around grid grid-cols-2 grid-rows-2 gap-4"
  >
    <div class="text-center" dir="ltr">
      <p class="font-bold text-base mb-4 p-2 text-nowrap">Registered Doctors</p>
      <div class="text-[35px]">
        {{ currentCount }}
      </div>
    </div>

    <div class="text-center" dir="ltr">
      <p class="font-bold text-base mb-4 p-2 text-nowrap">Active Doctors</p>
      <div class="text-[35px]">
        {{ currentCount }}
      </div>
    </div>

    <div class="text-center" dir="ltr">
      <p class="font-bold text-base mb-4 p-2 text-nowrap">Years of Experience</p>
      <div class="text-[35px]">
        {{ currentCount }}
      </div>
    </div>

    <div class="text-center text-nowrap" dir="ltr">
      <p class="font-bold text-base mb-4 p-2">Active Users</p>
      <div class="text-[35px]">
        {{ currentCount }}
      </div>
    </div>
  </section>
</template>

<script setup>
import { ref, onMounted } from "vue";


// Counter variable
const currentCount = ref(0);

// Variable for animation start time
let startTime = null;

// Counter animation function
const animateCount = (timestamp) => {
  // If the animation start time is not set, set it
  if (!startTime) {
    startTime = timestamp;
  }

  // Time elapsed since the start of the animation
  const elapsedTime = timestamp - startTime;

  // Calculate the counter value based on the elapsed time
  currentCount.value = Math.min(Math.round((elapsedTime / 2000) * 200), 200);

  // If we haven't reached the maximum value yet, continue
  if (currentCount.value < 200) {
    requestAnimationFrame(animateCount);
  }
};

// Function to check entry into the viewport
const handleIntersect = (entries) => {
  for (const entry of entries) {
    // If the component enters the viewport
    if (entry.isIntersecting) {
      // Start the counter animation
      requestAnimationFrame(animateCount);
    }
  }
};

// Ref variable to store the element to be observed
const elementToWatch = ref(null);

// Create an IntersectionObserver to observe the viewport
const observer = new IntersectionObserver(handleIntersect);
onMounted(() => {
  // Add the element to be observed
  observer.observe(elementToWatch.value);

});


</script>
<style scoped>
.bgchoose {
  background-color: #f0f9ff;
}

.border-2 {
  border-width: 2px;
}

.text-blue-900 {
  color: #1e3a8a;
}

.border-white {
  border-color: #ffffff;
}

.shadow-2xl {
  box-shadow: 0 25px 50px -12px rgb(0 0 0 / 0.25);
}

.rounded-3xl {
  border-radius: 1.5rem;
}

.my-10 {
  margin-top: 2.5rem;
  margin-bottom: 2.5rem;
}

.px-12 {
  padding-left: 3rem;
  padding-right: 3rem;
}

.py-5 {
  padding-top: 1.25rem;
  padding-bottom: 1.25rem;
}

.sm\\:w-full {
  width: 100%;
}



.mx-auto {
  margin-left: auto;
  margin-right: auto;
}

.sm\\:flex {
  display: flex;
}

.justify-around {
  justify-content: space-around;
}

.grid {
  display: grid;
}

.grid-cols-2 {
  grid-template-columns: repeat(2, minmax(0, 1fr));
}

.grid-rows-2 {
  grid-template-rows: repeat(2, minmax(0, 1fr));
}

.gap-4 {
  gap: 1rem;
}

.text-center {
  text-align: center;
}

.font-bold {
  font-weight: 700;
}

.text-base {
  font-size: 1rem;
}

.mb-4 {
  margin-bottom: 1rem;
}

.p-2 {
  padding: 0.5rem;
}

.text-nowrap {
  white-space: nowrap;
}



</style>