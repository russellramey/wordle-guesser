<template>
    <div id="App">
        <!-- CONTAINER-->
        <div id="Container">
        <h1>Wordle Guesser</h1>

        <!-- INPUTS -->
        <div id="Inputs">
            <!-- PRIMARY INPUTS -->
            <primary-character-group :data="state"></primary-character-group>

            <!-- SECONDARY INPUTS -->
            <secondary-character-group :data="state" :theme="'present'">
                <p>Word DOES conain letters:</p>
            </secondary-character-group>

            <!-- SECONDARY INPUTS -->
            <secondary-character-group :data="state" :theme="'absent'">
                <p>Word DOES NOT contain letters:</p>
            </secondary-character-group>
        </div>

        <!-- SUBMIT INPUTS -->
        <div id="Submit">
            <button @click="search" type="submit"> Search </button>
        </div>

        <!-- RESULTS -->
        <results :data="state.results"></results>
    </div>
    </div>
</template>

<script>
// Imports
import WordList from './data/wordlist'
import PrimaryCharacterGroup from './components/PrimaryCharacterGroup'
import SecondaryCharacterGroup from './components/SecondaryCharacterGroup'
import Results from './components/Results'
// Export
export default {
    name: 'App',
    components: {
        PrimaryCharacterGroup,
        SecondaryCharacterGroup,
        Results
    },
    data(){
        return{
            state:{
                wordlist: WordList,
                characters:{
                    primary: [null, null, null, null, null],
                    present: null,
                    absent: null
                },
                results: []
            },
            loading: false
        }
    },
    methods:{
        search(){
            // Reset results array
            this.state.results = this.state.wordlist.solutions;

            if(this.characterCount.length !== 0){
                console.log('filterPrimaryCharacters');
                this.state.results = this.filterPrimaryCharacters(this.state.results, this.state.characters.primary);
            }
            // Filter partial letters
            if(this.charactersPresent.length > 0){
                console.log('filterSecondaryCharacters');
                this.state.results = this.filterSecondaryCharacters(this.state.results, this.charactersPresent, 'present');
            }
            // Filter partial letters
            if(this.charactersAbsent.length > 0){
                console.log('filterSecondaryCharacters');
                this.state.results = this.filterSecondaryCharacters(this.state.results, this.charactersAbsent, 'absent');
            }

            // Sort results in alpha order
            this.state.results.sort();
        },
        filterPrimaryCharacters(wordlist, characters){
            // Results array
            let results = [];
            // For each character in array
            characters.forEach(function(value, index){
                // If value exists and is not blank
                if(value && value !== ''){
                    // Reset results, for next loop
                    results = [];
                    // Algorithum
                    wordlist.forEach(function(word){
                        if(word){
                            // Word array
                            word = word.split('');

                            // If value of word array matches letter value
                            if(word[index].toLowerCase() === characters[index].toLowerCase()){
                                // Push to results
                                results.push(word.join(''));
                            }
                        }
                    });
                    // Set new wordlist, for next loop
                    wordlist = results;
                }
            });

            // Return data, remove null values
            return results;
        },
        filterSecondaryCharacters(wordlist, characters, action){
            // Comparison
            let comparison;
            // For each value in wordlist array
            wordlist.forEach(function(value, index){
                // For each character in character array
                characters.forEach(function(character){
                    // Change comparison oporater based on action
                    if(action === 'present'){
                        comparison = (value ? !value.includes(character.toLowerCase()) : null);
                    } else {
                        comparison = (value ? value.includes(character.toLowerCase()) : null);
                    }
                    // If value and comparison are true
                    if(value && comparison){
                        wordlist[index] = null;
                    }
                });
            });

            // Return data
            return wordlist.filter(function(word){ return word != null; });
        }
    },
    computed:{
        characterCount(){
            return this.state.characters.primary.filter(function(letter){ return letter != null && letter != ''; });
        },
        charactersPresent(){
            return (this.state.characters.present ? this.state.characters.present.split('') : [])
        },
        charactersAbsent(){
            return (this.state.characters.absent ? this.state.characters.absent.split('') : [])
        }
    }
}
</script>

<style lang="scss">
    // Main styles
    @import './assets/scss/styles.scss';
</style>
