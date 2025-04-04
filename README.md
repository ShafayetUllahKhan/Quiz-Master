# Quiz-Master CODE:
#include <stdio.h>
#include <string.h>
#include <ctype.h>

// Structure to store quiz question, options, and correct answer
struct Question {
    char question[200]; // The question text
    char options[4][100]; // The four answer options
    char correctAnswer;  // The correct answer (A, B, C, D)
};

// Function to display the score
void displayScore(int score, int totalQuestions) {
    float percentage = (float)score / totalQuestions * 100;
    printf("\nYour total score: %d out of %d\n", score, totalQuestions);
    printf("Your percentage: %.2f%%\n", percentage);
}

// Function to ask a question and check the answer
int askQuestion(struct Question q) {
    char answer;
    int correct = 0;
    
    printf("\n%s\n", q.question);
    printf("A. %s\n", q.options[0]);
    printf("B. %s\n", q.options[1]);
    printf("C. %s\n", q.options[2]);
    printf("D. %s\n", q.options[3]);
    printf("Your answer (A, B, C, D): ");
    
    // Read player's answer
    scanf(" %c", &answer);
    answer = toupper(answer); // Convert answer to uppercase for consistency
    
    // Check if the player's answer is correct
    if (answer == q.correctAnswer) {
        correct = 1;
    }
    
    return correct;
}

// Function to ask difficulty and select the question set
void selectDifficulty(struct Question quiz[]) {
    int choice;
    printf("Welcome to the Quiz Game!\n");
    printf("Select your difficulty level:\n");
    printf("1. Easy\n");
    printf("2. Medium\n");
    printf("3. Hard\n");
    printf("Enter your choice (1/2/3): ");
    scanf("%d", &choice);

    switch (choice) {
        case 1:
        // Easy questions
            strcpy(quiz[0].question, "What is the capital of France?");
            strcpy(quiz[0].options[0], "Paris");
            strcpy(quiz[0].options[1], "London");
            strcpy(quiz[0].options[2], "Berlin");
            strcpy(quiz[0].options[3], "Madrid");
            quiz[0].correctAnswer = 'A';
            
            strcpy(quiz[1].question, "Which planet is known as the Red Planet?");
            strcpy(quiz[1].options[0], "Earth");
            strcpy(quiz[1].options[1], "Mars");
            strcpy(quiz[1].options[2], "Venus");
            strcpy(quiz[1].options[3], "Jupiter");
            quiz[1].correctAnswer = 'B';
            
            strcpy(quiz[2].question, "What is 2 + 2?");
            strcpy(quiz[2].options[0], "3");
            strcpy(quiz[2].options[1], "4");
            strcpy(quiz[2].options[2], "5");
            strcpy(quiz[2].options[3], "6");
            quiz[2].correctAnswer = 'B';
            break;
        
        case 2:
        // Medium questions
            strcpy(quiz[0].question, "Who wrote 'To Kill a Mockingbird'?");
            strcpy(quiz[0].options[0], "Harper Lee");
            strcpy(quiz[0].options[1], "J.K. Rowling");
            strcpy(quiz[0].options[2], "Mark Twain");
            strcpy(quiz[0].options[3], "F. Scott Fitzgerald");
            quiz[0].correctAnswer = 'A';
            
            strcpy(quiz[1].question, "What is the chemical symbol for water?");
            strcpy(quiz[1].options[0], "H2O");
            strcpy(quiz[1].options[1], "CO2");
            strcpy(quiz[1].options[2], "O2");
            strcpy(quiz[1].options[3], "NaCl");
            quiz[1].correctAnswer = 'A';
            
            strcpy(quiz[2].question, "Which element has the atomic number 1?");
            strcpy(quiz[2].options[0], "Helium");
            strcpy(quiz[2].options[1], "Hydrogen");
            strcpy(quiz[2].options[2], "Oxygen");
            strcpy(quiz[2].options[3], "Carbon");
            quiz[2].correctAnswer = 'B';
            break;
        
        case 3:
        // Hard questions
            strcpy(quiz[0].question, "What is the fastest land animal?");
            strcpy(quiz[0].options[0], "Lion");
            strcpy(quiz[0].options[1], "Cheetah");
            strcpy(quiz[0].options[2], "Leopard");
            strcpy(quiz[0].options[3], "Elephant");
            quiz[0].correctAnswer = 'B';
            
            strcpy(quiz[1].question, "Who developed the theory of relativity?");
            strcpy(quiz[1].options[0], "Isaac Newton");
            strcpy(quiz[1].options[1], "Albert Einstein");
            strcpy(quiz[1].options[2], "Galileo");
            strcpy(quiz[1].options[3], "Nikola Tesla");
            quiz[1].correctAnswer = 'B';
            
            strcpy(quiz[2].question, "Which programming language is known as 'C's successor'?");
            strcpy(quiz[2].options[0], "Java");
            strcpy(quiz[2].options[1], "C++");
            strcpy(quiz[2].options[2], "Python");
            strcpy(quiz[2].options[3], "Swift");
            quiz[2].correctAnswer = 'B';
            break;
    }
}

// Main function to drive the quiz game
int main() {
    struct Question quiz[3]; // Array of quiz questions
    int score = 0, totalQuestions = 3, i, correct;
    char playAgain;

    do {
        // Select the difficulty level
        selectDifficulty(quiz);

        // Timer and Score tracking
        printf("Quiz Started! Good luck!\n");

        for (i = 0; i < totalQuestions; i++) {
            correct = askQuestion(quiz[i]);
            score += correct; // Increment score if answer is correct

            // Display the score after each question
            printf("Your score so far: %d\n", score);
        }

        // Final score and feedback
        displayScore(score, totalQuestions);

        // Ask player if they want to play again
        printf("\nDo you want to play again? (Y/N): ");
        scanf(" %c", &playAgain);
        playAgain = toupper(playAgain); // Ensure it's uppercase

    } while (playAgain == 'Y'); // Keep playing if the user chooses 'Y'

    printf("Thanks for playing! Goodbye!\n");
    return 0;
}

