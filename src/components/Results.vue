<template>
    <div id="Results">
        <p><span>{{ data.length }}</span>SUGGESTIONS</p>
        <ul>
            <li v-for="value in data" :key="value">{{ value }}</li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'Results',
    props: {
        data: Array
    },
    computed:{
    }
}
</script>

<style lang="scss">
#Results{
    font-size: 1.5rem;
    font-weight: bolder;
    ul{
        list-style: none;
        text-align: center;
        margin: 0;
        padding: 0;
        text-transform: uppercase;
        font-weight: normal;
        display: flex;
        flex-wrap: wrap;
        li{
            width: 25%;
            text-align: center;
            padding: .25rem;
            @media screen and (max-width: 480px){
                width: 33.33333%
            }
        }
    }
    p span{
        margin-right: .5rem;
    }
}
</style>
