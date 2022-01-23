<template>
    <div class="SecondaryCharacterGroup">
        <div class="character-group">
            <div class="filter-input">
                <slot></slot>
                <template v-if="theme === 'present'">
                    <input v-model="data.characters.present" class="character character-present" type="text" style="" maxlength="5" v-on:keypress="isLetter" />
                </template>
                <template v-if="theme === 'absent'">
                    <input v-model="data.characters.absent" class="character character-absent" type="text" style="" maxlength="30" v-on:keypress="isLetter" />
                </template>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    name: 'PrimaryCharacterGroup',
    props: {
        data: Object,
        theme: String
    },
    methods:{
        isLetter(e) {
            let char = String.fromCharCode(e.keyCode); // Get the character
            if(/^[A-Za-z]+$/.test(char)) return true; // Match with regex
            else e.preventDefault(); // If not match, don't add to input text
        }
    }
}
</script>

<style lang="scss">
.SecondaryCharacterGroup{
    input{
        width:290px;
        &.character-present{
            background: #b59f3b;
        }
        &.character-absent{
            background: #3a3a3c;
        }
    }
}
</style>
