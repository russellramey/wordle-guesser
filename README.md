# Wordle-Guesser
Stuck on the latest [Wordle](https://www.powerlanguage.co.uk/wordle/)? Not anymore, Wordle-Guesser is a simple tool/application to help solve the daily Wordle. If you don't know what Wordle is, it is a daily 5 letter word guessing game. You too can play [Wordle](https://www.powerlanguage.co.uk/wordle/).

## URL
Use the [Wordle Guesser](https://russellramey.github.io/wordle-guesser/) GUI.

## How to use
As you play [Wordle](https://www.powerlanguage.co.uk/wordle/), you will get feedback as to how accurate you guess is. Using this feedback you can use this tool to narrow down your guesses, or simply use it to get inspired with your next guess.
1. Place known/correct letters found in the green tiles on Worlde, in the proper positions in the green inputs.
2. Place letters found in yellow tiles on Wordle, in the yellow input. (Only use alphanumeric characters)
3. Place letters found in the grey tiles on Wordle, in the grey input. (Only use alphanumeric characters)
4. Click the `Search` button to process the suggested words that fit your parameters.
5. Repeat each step as you gain more informative feedback from Wordle.

## How it works
Wordle-Guesser takes the available wordlist and preforms a series of filtering and sorting to reduce the total number of words from the wordlist. This filtering and sorting is performed as many times as needed (mainly based on how many characters are present in the multiple input fields).

## About
This was a quick weekend build idea I threw together after discovering the [Wordle](https://www.powerlanguage.co.uk/wordle/) game. Based on parameters passed it trys to figure out what the solution to the daily word puzzle is.

## Technology
- VueJS
- Javascript

## Support
To report a bug or have a question, create an issue on this repository.

## Project setup
```
npm install
```
### Compiles and hot-reloads for development
```
npm run serve
```
### Compiles and minifies for production
```
npm run build
```
