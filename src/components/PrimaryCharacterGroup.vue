<template>
    <div id="PrimaryCharacterGroup">
        <div class="character-group">
            <p>Known word letters and positions:</p>
            <ul>
                <li v-for="(character, index) in data.characters.primary" :key="index">
                    <input v-model="data.characters.primary[index]" class="character character-primary" type="text" maxlength="1" />
                </li>
            </ul>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PrimaryCharacterGroup',
    props: {
        data: Object
    }
}
</script>

<style lang="scss">
#PrimaryCharacterGroup{
    ul{
        display: flex;
        list-style: none;
        margin: 0;
        padding: 0;
        justify-content: center;
    }
    input.character-primary{
        background: #538d4e;
    }
}
</style>
