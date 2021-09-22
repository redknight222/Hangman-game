# Hangman-game
Hangman game
import random
names_ = ['python', 'java', 'kotlin', 'javascript']
random.shuffle(names_)

print('H A N G M A N')
game = input('Type "play" to play the game, "exit" to quit:')
base_word = names_[1]
user_word = list('-' * len(base_word))
repeats = set()
i = 0
if game == 'play':
    while True:
        if i == 8:
            print('You lost!')
            break
        elif ''.join(user_word) == base_word:
            print('''You guessed the word!
You survived!''')
            break
        print("")
        print(''.join(user_word))
        letter = input('Input a letter:')
        if letter in repeats:
            print("You've already guessed this letter")
            continue
        elif letter.isspace() or len(letter) > 1:
            print('You should input a single letter')
            continue
        elif letter.isupper() or not letter.isalpha():
            print('Please enter a lowercase English letter')
            continue
        else:
            for a in range(len(base_word)):
                if base_word[a] == letter:
                    user_word[a] = letter
                    repeats.add(letter)
                elif letter not in base_word:
                    i += 1
                    repeats.add(letter)
                    print("That letter doesn't appear in the word")
                    break
elif game == 'exit':
    pass
else:
    print()
    game = input('Type "play" to play the game, "exit" to quit:')
