<template>
    <div>
        <div class=" flex flex-col">
            <div class="navbar bg-base-100">
                <div class="flex-1">
                    <a @click="handleHome" class="btn btn-ghost normal-case text-xl">Home</a>
                </div>
                <div class="flex-none">
                    <ul class="menu menu-horizontal px-1">
                        <li @click="handleRegister"><a>Register</a></li>
                    </ul>
                </div>
            </div>
            <div >
                <div >
                    <slot />
                </div>
            </div>
        </div>

    </div>
</template>

<script setup>
const handleRegister = () => {
    navigateTo('/register')
}

const handleHome = () => {
    navigateTo('/')
}
</script>

<style lang="scss" scoped></style>