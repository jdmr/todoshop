<template>
    <div class="min-h-screen grid grid-rows-[auto_1fr_auto]">
        <header class="bg-blue">
            <nav class="md:flex md:items-center md:justify-between">
                <div class="flex justify-between items-center">
                    <button @click="goto('/')">TodoSHOP</button>
                    <div class="md:hidden">
                        <button @click="toggleMenu">MENU</button>
                    </div>
                </div>

                <div id="menuDiv" class="hidden flex-col md:flex md:flex-row">
                    <button
                        class="p-2 text-left hover:bg-blue-300"
                        @click="goto('/about')"
                    >
                        About
                    </button>
                    <button
                        class="p-2 text-left hover:bg-blue-300"
                        @click="goto('/contact')"
                    >
                        Contact
                    </button>
                </div>
            </nav>
        </header>
        <div>
            <RouterView />
        </div>
        <footer class="bg-blue">
            <div>Footer</div>
        </footer>
    </div>
</template>

<script setup lang="ts">
import { useRouter } from 'vue-router'

const router = useRouter()
const goto = (path: string) => {
    router.push(path)
    const el = document.getElementById('menuDiv')
    if (!el) return
    if (el.classList.contains('hidden')) return
    toggleMenu()
}
const toggleMenu = () => {
    const el = document.getElementById('menuDiv')
    if (!el) return
    if (el.classList.contains('hidden')) {
        el.classList.replace('hidden', 'flex')
    } else {
        el.classList.replace('flex', 'hidden')
    }
}
</script>
