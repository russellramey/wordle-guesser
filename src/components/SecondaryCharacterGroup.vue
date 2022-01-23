<template>
    <div class="SecondaryCharacterGroup">
        <div class="character-group">
            <div class="filter-input">
                <slot></slot>
                <template v-if="theme === 'present'">
                    <input v-model="data.characters.present" class="character character-present" type="text" style="" maxlength="5" />
                </template>
                <template v-if="theme === 'absent'">
                    <input v-model="data.characters.absent" class="character character-absent" type="text" style="" maxlength="30" />
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
