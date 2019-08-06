<template>
    <div>
        <nav class="navbar navbar-light bg-light">
            <h3>Cindy Stitches</h3>

            <router-link :to="{name: 'createnew'}">
            <button>Create New</button>
            </router-link>
        </nav>
    </div>
</template>

<style scoped>
    h3 {
        color:#148489;
    }
    button {
        background: #148489;
        float: right;
    }
    button:hover {
        background: #ffffff;
    }
</style>
