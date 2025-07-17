<template>
    <div class="h-50 justify-center content-center bg-cover bg-no-repeat bg-center md:h-55 lg:h-60" :style="{ backgroundImage: `url(${bgurl})`}">
        <div class="flex items-center gap-4 justify-center m-4">
            <img
                alt=""
                src="../assets/profile.webp"
                class="size-30 md:size-35 lg:size-40 object-cover animate-rotate-border max-w-sm transition-all duration-500 ease-out transform-3d rounded-lg cursor-pointer hover:scale-[1.03] bg-conic/[from_var(--border-angle)] to-black from-80% via-90% to-100% p-[2px]"/>
            <div>
                <h3 class="font-medium text-gray-900 text-lg md:text-[24px] lg:text-[30px]">Software Engineer</h3>
            
                <p class="mt-0.5 text-gray-700 text-[12px] md:text-[18px] lg:text-[20px]">
                    Hey, I’m Giri Shaffaat. <br>In my free time, I design & develop apps to make my life easier.
                </p>
            </div>
        </div>
    </div>
    
  </template>

<script setup>
    import bgurl from '../assets/profile-bg.webp'
</script>