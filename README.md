# C-
Fishing Game
#include <iostream>
#include <cstdlib>
#include <ctime>
#include <string>

using namespace std;

// prototypes
int rollDie();
string getCatch(int roll);
int getPoints(int roll);
string getFinalMessage(int totalPoints);

int main() {
    srand(time(0)); 
    int totalPoints = 0;
    char continueFishing;

    cout << "    Let's Go Fishing!!\n";
    cout << "**************************\n\n";
    cout << "        Cast away!\n";
    cout << "**************************\n";
    
    do {
        // Simulate a die roll and get the catch
        int roll = rollDie();
        string catchItem = getCatch(roll);
        int points = getPoints(roll);

        // Update points
        totalPoints += points;

        // Display fish
        cout << "You caught " << catchItem << "!\n\n";
        cout << "Fish another round? (y/n): ";
        cin >> continueFishing;

    } while (continueFishing == 'y' || continueFishing == 'Y');

    // Display nresults
    cout << "\nYour fishing score\n";
    cout << "********************\n\n";
    cout << "Total Points: " << totalPoints << endl;
    cout << getFinalMessage(totalPoints) << endl;

    return 0;
}

// Function to simulate rolling a six-sided die
int rollDie() {
    return (rand() % 6) + 1;
}

// fish
string getCatch(int roll) {
    switch (roll) {
        case 1: return "a gigantic fish";
        case 2: return "an old shoe";
        case 3: return "a tiny fish";
        case 4: return "a black pearl";
        case 5: return "an old beer can";
        case 6: return "a treasure chest";
        default: return "nothing";
    }
}

// assign points
int getPoints(int roll) {
    switch (roll) {
        case 1: return 10; 
        case 2: return -2;  
        case 3: return 4;  
        case 4: return 15; 
        case 5: return -4;  
        case 6: return 16;  
        default: return 0;
    }
}

// final message
string getFinalMessage(int totalPoints) {
    if (totalPoints >= 30) {
        return "You're an Expert fisher!!";
    } else if (totalPoints >= 15) {
        return "You caught some good stuff, but you need more practice!";
    } else if (totalPoints >= 5) {
        return "Don't give up! keep fishing.";
    } else {
        return "Better luck next time. Keep fishing!";
    }
}
