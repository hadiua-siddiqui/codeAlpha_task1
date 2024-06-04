# codeAlpha_task1
#include <iostream>
#include <cstdlib>
#include <ctime>
using namespace std;

int main()
{
    int num, guess, tries = 0;
    srand(time(0)); 
    num = rand() % 100 + 1; 
    cout << "Welcome To Numbere Guessing Game\n\n";

    do
    {
        cout << "Guess a number between 1 and 100 : ";
        cin >> guess;
        tries++;

        if (guess > num)
            cout << "Too high!\n\n";
        else if (guess < num)
            cout << "Too low!\n\n";
        else
            cout << "\n YOU GUESS THE CORRECT NUMBER  " << tries << " guesses!\n";
    } while (guess!= num);

    return 0;
}
