Number Guessing game

CODE IN C++--

#include #include #include

using namespace std;

int getFeedback(int guess, int secretNumber) { if (guess == secretNumber) { cout << "Congratulations! You guessed the correct number " << secretNumber << ".\n"; return 0; } else if (guess < secretNumber) { cout << "Too low! Try a higher number.\n"; return -1; } else { cout << "Too high! Try a lower number.\n"; return 1; } }

void playGame(int rangeStart, int rangeEnd, const string &userName) { srand(static_cast(time(0))); int secretNumber = rand() % (rangeEnd - rangeStart + 1) + rangeStart;

cout << "Welcome, " << userName << ", to the Number Guessing Game!\n";
cout << "I have selected a random number between " << rangeStart << " and " << rangeEnd << ". Try to guess it.\n";

int attempts = 0;
int guess;

do
{
    cout << "Enter your guess: ";
    cin >> guess;
    attempts++;

    int feedback = getFeedback(guess, secretNumber);

    if (feedback == 0)
    {
        cout << "You guessed the correct number in " << attempts << " attempts.\n";
        return;
    }

    if (attempts == 3)
    {
        cout << "You've reached 3 attempts. Here's a hint: the number is divisible by 2.\n";
    }

} while (attempts < 5);

cout << "You've reached 5 attempts. The correct number was " << secretNumber << ". Better luck next time, " << userName << "!\n";
}

int main() {

string userName; cout << "Enter your name: "; getline(cin, userName);

int rangeStart, rangeEnd;
cout << "Enter the range for the number (e.g., 1 200): ";
cin >> rangeStart >> rangeEnd;

playGame(rangeStart, rangeEnd, userName);

return 0;
}
