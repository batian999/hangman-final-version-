# hangman-final-version-

# This function is to test if the letters are in the secret word. If the letters are in the secret word, the letter will be print out in the right position while other letters will be replaced by underscore first. 
# The newWord represents the process that user takes the right guesses and right letters and underscores that will be print out. 
def wordSoFar(correctLetter, secretWord):
    newWord = ""
    for letter in secretWord:
        if letter in correctLetter: 
# This is to store the right guesses letter in the new word. 
            newWord = newWord + letter
# This is to use underscore to represent the letters that haven't been guessed.
        else:
            newWord = newWord + " _"
    return newWord

#main 
import random
# This is to reset the good guess to 0 and add up later. It is for the guessed letters that are in the secret word. When the good guesses equals the number of letters in secret word, the user wins. 
GOODGUESS = 0
# This is to reset the bad guess to 0 and add up later. It is for the guessed letters that are not in the secret word.
# When the bad guesses equal to 10, the game will be over. 
BADGUESS = 0 
WORDLIST = ["hi","stupid","smart","laugh","ugh"]
# This is to select a word randomly.
secret_word = random.choice(WORDLIST)
# This is to add guessed letters together and check if the letters have been inputted or not. 
letter_list = " "
# This is to store the letters that are in the secret word.
correct_letter = " "
# This is a while loop that limits the bad guess to 10 times. 
GameOver = False 
while not GameOver:
# This is to tell the user to input a letter. 
    guess = input("Enter a letter that you think is in the secret word: ")
# This is for testing whether the guess has been inputted or not. If so, print change one letter; if not, add this new letter to the letter list, which records all the letters that have been tested. 
    if guess in letter_list:
        print("You have already given this one! Change one letter!")
    else: 
        letter_list = letter_list + guess 
# This if loop is for testing whether the guess is in the secret word. If so, add the letter to the correct letter list, and the good guess will add 1. 
        if guess in secret_word:
            correct_letter = correct_letter + guess
            GOODGUESS = GOODGUESS + 1
# This is to call the function wordSoFar and put the value of correct letters and secret words in the function and print the letters I have and the letters I don not have yet by underscore.             
            print(wordSoFar(correct_letter, secret_word))
# This is for getting to know how many letters left by subtracting the good guess from how many letters the secret word has.        
            letter_left = len(secret_word) - GOODGUESS
            print("Congratulations! You have", letter_left, "letter(s) left.")
# This is for testing whether the letters in the secret word have all been inputted, so that the user is win and the loop will be broke. 
            if letter_left == 0:
                print("You win!")
                GameOver = True
# This is for that if the guess is not in the secret word, the bad guess will increments by 1, and chances left is got by subtracting bad guess from 10 chances, so that the readers know how many chances they have left. 
        else: 
            BADGUESS = BADGUESS+1
            chances_left = 10 - BADGUESS
            print("This is not the correct letter! You only have", chances_left, "chance(s) left!")
# If the chances left is equal to 0, which means the user has been used all the 10 chances, the user loses the game and game is over. 
            if chances_left == 0:
                print("Game Over!")
                GameOver = True
