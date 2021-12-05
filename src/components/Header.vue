<template>
        <div>
            <ul>
                <li><a href="#">Github Profile Finder</a></li>
                <li>Theme Switch</li>
            </ul>
        </div>
</template>

<script>


export default{
    name: 'Header',
  
}
</script>

<style scoped>
    ul {
        display: flex;
        justify-content: space-between;
        padding: 0;
    }

    li {
        list-style: none;
    }

    li a {
        text-decoration:  none;
        font-size: 1.5em
    }
</style>
