<template>
    <div class="border border-violet-800 fixed top-0 bg-white z-50 w-full text-black-900  py-3 md:text-xl flex justify-center ">
        <div class="flex w-full justify-between px-3 sm:px-4 md:px-8 lg:w-[1000px] ">
            <div>
                <p>Diana</p>
            </div>
            <div class="space-x-3">
                <NuxtLink class="hover:bg-slate-300"  :to="{ path: '/', hash: '#maps'}">maps</NuxtLink>
                <NuxtLink class="hover:bg-slate-300"  :to="{  path: '/', hash: '#chart-covid' }">chart</NuxtLink>
            </div>
        </div>
    </div>
</template>