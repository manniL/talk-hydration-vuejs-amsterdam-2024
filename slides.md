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
layout: intro
---

# Okay... But how can that *fail*?

<VClicks>

## <span class="underline">Different state</span> on the server and on the client

</VClicks>

---

# Invalid HTML

---

# Invalid HTML

````md magic-move
```html
<p>
 <div>some words</div>
</p>
```
```html
<p>
 some words
</p>
```
````

<VClicks at="1">

* Invalid HTML will be fixed by the browser but is sent "as is" by the server
* This leads to different DOM trees and thus different hydration results
* **Solution:** **Validate your HTML**, e.g. with `@nuxtjs/html-validator`

</VClicks>

---

# Scripts manipulating your HTML

---

# Scripts manipulating your HTML

In the rendered HTML

````md magic-move
```html
<span class="relative z-20">
  <!--[-->
  View all talks
  <!--]-->
</span>
```
```html
<span class="relative z-20">
  View all talks
</span>
```
````

<VClicks at="1">

* Scripts that manipulate the final rendered HTML can cause problems
* This can be various optimization scripts, e.g. Cloudflare's optimization scripts
* Removing placeholder comments will lead to hydration issues...
* ...because the client can't match the server's HTML anymore
* **Solution:** **Disable these scripts**

</VClicks>

---

# Different data on the server and client

````md magic-move
```ts
// In the script part of a Vue component (Nuxt app)
const value = ref(Math.random())
```
```ts
// In the script part of a Vue component (Nuxt app)
const value = ref(Math.random())
```
```ts
// In the script part of a Vue component (Nuxt app)
const value = ref(Math.random())
```
```ts
// In the script part of a Vue component (Nuxt app)
const value = useState('unique-key', Math.random())
```
````

<VClicks at="1">

* Different data on the server and client will lead to hydration mismatches
* Especially when using `Date`, `Math.random()` or other varying values, this can happen
* **Solution:** **Transfer these values to the server**

</VClicks>

---

# `import.meta.client` (e.g. with auth check)

---

# `import.meta.client` (e.g. with auth check)

```vue
<script setup>
const isLoggedIn = ref(false)
if(import.meta.client) {
  isLoggedIn.value = true // imagine some auth check here
}
</script>

<template>
  <div v-if="isLoggedIn">
    <h1>You are in!</h1>
  </div>
  <div v-else>
    <h1>Please log in</h1>
  </div>
</template>
```

<VClicks at="1">

* Changing state in `import.meta.client` can cause hydration errors
* It essentially changes the values the "client expects" from the server
* **Solution:** **Execute client-only code in `onBeforeMount` or `onMounted`**

</VClicks>
---

# Various other cases

<VClicks>

* This is not an exhaustive list
* There are many other cases that can lead to hydration mismatches
* Eventually, you can debug them though!

</VClicks>

---

# Debugging hydration mismatches

<img class="mb-8" src="/hydration/better-error-message.png" />

<VClicks depth="2">

* Vue 3.4 improved hydration messages
* You can check them in production via `__VUE_PROD_HYDRATION_MISMATCH_DETAILS__` compile-time flag (or `debug: true` in Nuxt)
* Also Julien's `nuxt-hydration` module can help you with that


</VClicks>

<!-- TODO: Screenshot hydration module -->

---
layout: intro
---

# Can we avoid hydration?

---

# Can we avoid hydration?

<VClicks depth="2">

* Yes - by not including JavaScript at all!
  * e.g. via `experimentalNoScripts` route rule in Nuxt
  * Problem: No interactivity 😫. If JS is needed, you need to write it vanilla.
* You could try inferring data from markup (not easily possible)
  * This won't work for complex scenarios though
* But you can two things: Decide **what** should be hydrated and **when**!

</VClicks>

---

# **What** to hydrate (Partial Hydration)

<VClicks depth="2">

* e.g. possible via **Island Architecture** (with Astro or îles)
* Idea: Only hydrate what needs to be interactive
* Especially good with static, content-heavy sites

</VClicks>

<!-- TODO: Graphic -->

---

# **When** to hydrate (Progressive/Lazy Hydration)

<VClicks depth="2">

* Idea: Delay hydration to a later point
  * e.g. on scroll, on click or on browser idle
* This improves the initial load time
* If not being careful, this can lead to a waiting time on click though (bad _INP_)
* Can be done via Harlan's `nuxt-delay-hydration` module

</VClicks>

---

# What if...

<VClicks>

* We could render components on the server only...
* Wouldn't need hydration for them...
* They could still be "interactive"...
* And could also render client-side components?

</VClicks>

---
layout: intro
---

# Nuxt Server Components - "Reversed Islands"

<VClicks>

## Watch Julien Huang's talk later

</VClicks>

---
layout: intro
---

# What's next in terms of hydration and Vue.js?

---

# What's next in terms of hydration and Vue.js?

<VClicks>

* `useId` composable in Vue 3.5
  * Already available in Nuxt to fill the gap
  * Why? To provide unique ids, e.g. for accessibility attributes like `aria-labelledby`
* A hook to react when mismatches happen (https://github.com/vuejs/core/pull/8389)
* More improvements with regards to lazy hydration, ssr-only etc. etc. in future Vue versions possible
* Let's see what Vapor Mode will bring 👀

</VClicks>

---

# Recommendations for a better hydration experience with Vue + Nuxt

<VClicks>

* `nuxt-delay-hydration` until native support
* `nuxt-hydration` to debug hydration mismatches
* `@nuxtjs/html-validator` to ensure your HTML is valid
* Error Logging and Tracking through a service of your choice

</VClicks>


---

# Summary

<VClicks depth="2">

* Hydration is necessary when using Vue + SSR
* Hydration mismatches can happen due to various reasons...
  * ...but they can be debugged and fixed easier now
* Hydration experience can be improved with modules and server components
* Future Hydration improvements are planned!

</VClicks>

---
layout: intro
---

# <span class="water-font water-font-first">Hydration Demystified</span><span class="water-font water-font-second" aria-hidden>Hydration Demystified</span>

# <mdi-check class="text-green-500 mt-32 invisible" />

<style>
@import url("https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900");

  h1 {
    @apply relative w-full !text-7xl !mt-0 !mb-0; 
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
layout: intro
---

# <span class="water-font water-font-first">Hydration Demystified</span><span class="water-font water-font-second" aria-hidden>Hydration Demystified</span>

# <mdi-check class="text-green-500 mt-32" />

<style>
@import url("https://fonts.googleapis.com/css?family=Poppins:100,200,300,400,500,600,700,800,900");

  h1 {
    @apply relative w-full !text-7xl !mt-0 !mb-0;
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
}
</style>

---
layout: intro
---

# One more thing...


<div class="justify-around flex">
<VClicks>

<div>
<img src="https://michaelnthiessen.com/profile.jpg" alt="Michael Thiessen" class="rounded-full w-32 h-32 mx-auto" />
<h2 class="mt-4">Michael Thiessen</h2>
</div>

<div>
<img src="https://lichter.io/img/me@2x.jpg" alt="Alexander Lichter" class="rounded-full w-32 h-32 mx-auto" />
<h2 class="mt-4">Alexander Lichter</h2>
</div>

</VClicks>
</div>


---
preload: false
---

<div class="justify-center items-center flex w-full h-full">
  <div class="luminance py-4">
  DejaVue
  </div>
</div>

<style>
.luminance {
   background: 50% 100% / 50% 50% no-repeat
              radial-gradient(ellipse at bottom, #fff, transparent, transparent);
  -webkit-background-clip: text;
  background-clip: text;
  color: transparent;
  font-size: 10vw;
  font-family: "Source Sans Pro", sans-serif;
  animation: reveal 3000ms ease-in-out forwards 200ms,
             glow 2500ms linear infinite 2000ms;

  @keyframes reveal {
    80%{
      letter-spacing: 8px;
    }
    100% {
      background-size: 300% 300%;
    }
  }
  @keyframes glow {
    40% {
      text-shadow: 0 0 8px #fff;
    }
  }
}
</style>

---
layout: intro
---

<div class="justify-center items-center">
<div class="font-src text-6xl py-4" style="text-shadow: 0 0 200px #fff;">DejaVue</div>

## March 2024

# `https://dejavue.fm` 

<Qrcode url="https://dejavue.fm" class="mt-8 mx-auto" />

</div>

<style>
h1 {
  @apply !text-4xl !mt-16;
}

h2 {
  @apply !text-xl;
}

.font-src {
  font-family: "Source Sans Pro", sans-serif;
}
</style>

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