<template>
    <div class="md:h-[100vh] bg-blue-950  text-white flex md:justify-center md:items-center">
        <div class="flex  flex-col-reverse md:flex-row md:justify-between px-4 md:w-[1000px]">
            <div class="md:max-w-[30%] py-2 flex flex-col px-4 items-center space-y-5 backdrop-blur-sm bg-white/30">
                <div class="flex space-x-2 md:space-x-0 md:flex-col">
                    <p class="text-base md:text-3xl ">Pandemi COVID-19 di Indonesia</p>
                </div>
                <div>
                    Pandemi Covid-19 di Indonesia merupakan bagian dari pandemi penyakit koronavirus 2019 (Covid-19) yang sedang berlangsung di seluruh dunia. Penyakit ini disebabkan oleh koronavirus sindrom pernapasan akut berat 2 (SARS-CoV-2).
                </div>
            </div>
            <div class="md:hidden flex justify-center">
                <NuxtImg src="/monas.jpg" width="full" height="200" />
            </div>
            <div class="hidden md:flex">
                <NuxtImg src="/monas.jpg" width="full" height="500" />
            </div>

        </div>
    </div>
</template>