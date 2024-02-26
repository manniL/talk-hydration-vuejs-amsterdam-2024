---
theme: ./theme
title: "Nuxt 3 - Just Vue and a bit of Magic?"
website: lichter.io
handle: TheAlexLichter
favicon: https://lichter.io/img/me@2x.jpg
highlighter: shiki
lineNumbers: true
layout: intro
transition: fade
---

---

<img src="/hydration/cryptic-error.png">

---
layout: intro
preload: false
transition: false
---

<img v-motion :initial="{ scale: 1, x: 0 }" :enter="{ scale: 3, x: 750, transition: { duration: 500 } }" src="/hydration/cryptic-error.png">


---
layout: intro
---

<img src="/hydration/warning-dev.png">

---
layout: intro
---

<img v-motion :initial="{ scale: 1, x: 0 }" :enter="{ scale: 3, x: 750, transition: { duration: 500 } }" src="/hydration/warning-dev.png">

---
preload: false
---

<img v-motion :initial="{ y: 500 }" :enter="{ y:0, transition: { duration: 1000 } }" src="/angry.png" />

---
layout: intro
---

## Vue.js <logos-vue class="text-4xl pt-4" />

# <span class="water-font water-font-first">Hydration Demystified</span><span class="water-font water-font-second" aria-hidden>Hydration Demystified</span>

### Vue.js <span class="text-[#e87737]">Amsterdam</span> 2024

<style>
@import url("https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900");

  h1 {
    @apply relative w-full !text-7xl !mt-28 !mb-64; 
  }

  h2 {
    @apply !text-4xl;
  }

  h3 {
    @apply !text-2xl;
  }

.water-font {
	font-family: "Poppins", sans-serif;
	transform: translate(-50%, -50%);

  @apply text-white absolute w-full;
}

</style>

---
layout: intro
---


## Vue.js <logos-vue class="text-4xl pt-4" />

# <span class="water-font water-font-first">Hydration Demystified</span><span class="water-font water-font-second" aria-hidden>Hydration Demystified</span>

### Vue.js <span class="text-[#e87737]">Amsterdam</span> 2024

<style>
@import url("https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900");

  h1 {
    @apply relative w-full !text-7xl !mt-28 !mb-64; 
  }

  h2 {
    @apply !text-4xl;
  }

  h3 {
    @apply !text-2xl;
  }

.water-font {
	font-family: "Poppins", sans-serif;
	transform: translate(-50%, -50%);

  @apply text-white absolute w-full;
}

.water-font-first {
  @apply text-transparent;
	-webkit-text-stroke: 1px #03a9f4;
}

.water-font-second {
	color: #03a9f4;
	animation: animate 4s ease-in-out infinite;
}

@keyframes animate {
	0%,
	100% {
		clip-path: polygon(
			0% 45%,
			16% 44%,
			33% 50%,
			54% 60%,
			70% 61%,
			84% 59%,
			100% 52%,
			100% 100%,
			0% 100%
		);
	}

	50% {
		clip-path: polygon(
			0% 60%,
			15% 65%,
			34% 66%,
			51% 62%,
			67% 50%,
			84% 45%,
			100% 46%,
			100% 100%,
			0% 100%
		);
	}
}
</style>

---
layout: two-cols
heading: About me
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
  <img class="w-75 rounded-full" src="https://lichter.io/img/me@2x.webp" />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>
<VClicks class="space-y-2 mt-10 text-xl h-full">

* <mdi-account-check class="dark:text-green-100 text-green-700" /> **Web Engineering Consultant**
* <mdi-microphone /> Speaker & Instructor
* <logos-nuxt-icon /> Nuxt.js Team
* <mdi-twitter class="text-blue-400" /><mdi-youtube class="text-red-500" /><mdi-twitch class="text-purple-700" /> @TheAlexLichter
* <mdi-web /> [https://lichter.io](https://lichter.io)
* <mdi-github /> [manniL](https://github.com/manniL)

</VClicks>
</template>

---
layout: intro
---

# Do you use SSR?

<VClicks>

## If not, you never bother with hydration errors

</VClicks>

---
layout: intro
---

# What is Hydration?

<!-- 
 Why are JavaScript developers so thirsty? 
-->

---

<HydrationStepOne class="h-90 w-full" />

---

<HydrationStepTwo class="h-90 w-full" />

---

<HydrationStepThree class="h-90 w-full" />

---

<HydrationStepFour class="h-90 w-full" />

---

<HydrationStepFive class="h-90 w-full" />

---

<HydrationStepSix class="h-90 w-full" />

---

<HydrationStepSeven class="h-90 w-full" />

---

<HydrationStepEight class="h-90 w-full" />

---

<HydrationStepNine class="h-90 w-full" />


---

# Serializing State from Server to Client

`example.com/_payload.json`

```json
[
  { "data": 1, "prerenderedAt": 209 },
  ["Reactive", 2],
  {
    "latest-articles": 3,
    "latest-speaking": 74,
    "latest-workshops": 166
  },
  [4, 26, 43, 58],
  {
    "_path": 5,
    "_dir": 6,
    "_draft": 7,
    "_partial": 7,
    "_locale": 8,
    "title": 9,
  },
  1708189751754
]
```

---

TODO FROM HERE

* What is hydration?

* How can it mismatch => * Different data fetching on client and server
  * Invalid HTML
  * Scripts manipulating your HTML (e.g. removing placeholder comments)
  * Calculating values based on changing data (think of `Date` or `Random`) on client and server separately
  * Authentication state

* Can we avoid hydration?
  * No JavaScript
  * Infer data from markup
    * Won't work for complex scenarios
  * First of all, we can delay it (progressive/lazy hydration)
    * But does this always help? 
    * Faster initial load but almost guaranteed waiting time on click
  * Ideally, we also only decide what to hydrate (partial hydration)
  * Island Architecture (e.g. with Astro) to only hydrate what needs to be interactive
    * Especially good with static, content-heavy sites
  * Nuxt Server Components -> Julien's talk later

* Vue 3.4 improved hydration messages + option to check them also in production
* vue-bind-once (https://github.com/danielroe/vue-bind-once)
* Upcoming: Vue-based useId composable planned for v3.5 (https://twitter.com/youyuxi/status/1745379112456429688)
* Upcoming: Mismatched hook (https://github.com/vuejs/core/pull/8389)
* And more to come in future Vue (and also Nuxt) versions

What to recommend:

* https://github.com/harlan-zw/nuxt-delay-hydration
* https://github.com/huang-julien/nuxt-hydration
* https://github.com/nuxt-modules/html-validator
* Error Logging and Tracking through a service of your choice


---

---
layout: intro
preload: false
---

<h1 v-motion :initial="{ y: 0 }" :enter="{ y: -500, transition: { duration: 750, delay: 250 } }" class="mt-12 flex justify-center items-center">

<logos-vue class="text-8xl"/>
<mdi-heart class="text-red-500 text-8xl" />

</h1>

---

# Summary

TODO

---
layout: intro
---

# Thanks a lot to my sponsors!
<img src="https://raw.githubusercontent.com/manniL/static/main/sponsors.svg" class="h-80 mx-auto" alt="My GitHub sponsors">

---
layout: two-cols
heading: Thank you for your attention!
---

<template v-slot:default>
<div class="flex flex-col justify-center items-center h-full">
<img
  class="w-75 rounded-full"
  src="https://lichter.io/img/me@2x.webp"
  />
  <h2 class="mt-4">Alexander Lichter</h2>
</div>
</template>

<template v-slot:right>

* <mdi-account-check class="dark:text-green-100 text-green-700" /> **Web Engineering Consultant**
* <mdi-microphone /> Speaker & Instructor
* <logos-nuxt-icon /> Nuxt.js Team
* <mdi-twitter class="text-blue-400" /><mdi-youtube class="text-red-500" /><mdi-twitch class="text-purple-700" /> @TheAlexLichter
* <mdi-web /> [https://lichter.io](https://lichter.io)
* <mdi-github /> [manniL](https://github.com/manniL)

</template>

<style>
  ul {
    @apply space-y-2 mt-10 text-xl h-full;
  }
</style>

---
layout: intro
hideLogoInCorner: true
---

# Slides / Repo

* Slides: [https://lichter.link/vueams-24/](https://lichter.link/vueams-24/)

<div class="flex mx-32 justify-around">

<LightOrDark>
<template #light>
  <img class="w-32 h-32 mt-16 mx-auto" src="https://raw.githubusercontent.com/manniL/static/main/logo-lightbulb-black-red.svg" />
</template>
<template #dark>
  <img class="w-32 h-32 mt-16 mx-auto" src="https://raw.githubusercontent.com/manniL/static/main/logo-lightbulb-white-red.svg" />
</template>
</LightOrDark>

<Qrcode url="https://lichter.link/vueams-24/" class="mt-8 mx-auto" note="Slides" />

</div>

<style>
  ul {
    @apply list-none!;
  }
</style>