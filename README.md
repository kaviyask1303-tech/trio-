# trio-
import random

class PuzzleGame:
    def __init__(self):
        self.target = random.randint(1, 100)
        self.attempts = 0
        self.max_attempts = 7
    
    def play(self):
        print("=" * 50)
        print("Welcome to the Number Guessing Puzzle Game!")
        print("=" * 50)
        print(f"I'm thinking of a number between 1 and 100.")
        print(f"You have {self.max_attempts} attempts to guess it.\n")
        
        while self.attempts < self.max_attempts:
            try:
                guess = int(input("Enter your guess: "))
                
                if guess < 1 or guess > 100:
                    print("Please enter a number between 1 and 100.\n")
                    continue
                
                self.attempts += 1
                
                if guess == self.target:
                    self.win()
                    return
                elif guess < self.target:
                    print(f"Too low! Try a higher number. ({self.max_attempts - self.attempts} attempts left)\n")
                else:
                    print(f"Too high! Try a lower number. ({self.max_attempts - self.attempts} attempts left)\n")
            
            except ValueError:
                print("Invalid input! Please enter a valid number.\n")
        
        self.lose()
    
    def win(self):
        print("=" * 50)
        print(f"🎉 Congratulations! You guessed the number {self.target}!")
        print(f"You solved it in {self.attempts} attempts!")
        print("=" * 50)
    
    def lose(self):
        print("=" * 50)
        print(f"Game Over! The number was {self.target}.")
        print(f"Better luck next time!")
        print("=" * 50)

if __name__ == "__main__":
    game = PuzzleGame()
    game.play()
    
    while True:
        play_again = input("\nDo you want to play again? (yes/no): ").lower()
        if play_again == "yes":
            game = PuzzleGame()
            game.play()
        elif play_again == "no":
            print("Thanks for playing! Goodbye!")
            break
        else:
            print("Please enter 'yes' or 'no'.")
