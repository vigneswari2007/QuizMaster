# QuizMaster
This program is a multiple-choice quiz application designed to test a user's knowledge on a specific topic. It presents a series of questions, accepts user answers, provides immediate feedback on correctness, and automatically calculates and displays a final score.
#include <stdio.h>
#include <string.h>

// Structure to hold question data
typedef struct {
    char question[256];M
    char options[4][64]; // Up to 4 options for each question
    int correct_option;  // Index of the correct option (0-3)
} Question;

int main() {
    // Define an array of questions
    Question quiz[] = {
        {"What is the capital of France?", {"London", "Paris", "Rome", "Berlin"}, 1},
        {"Which planet is known as the Red Planet?", {"Earth", "Mars", "Jupiter", "Venus"}, 1},
        {"What is 2 + 2?", {"3", "4", "5", "6"}, 1}
    };

    int num_questions = sizeof(quiz) / sizeof(quiz[0]);
    int score = 0;
    int user_answer;

    printf("Welcome to the C Quiz!\n\n");

    for (int i = 0; i < num_questions; i++) {
        printf("Question %d: %s\n", i + 1, quiz[i].question);
        for (int j = 0; j < 4; j++) {
            printf("%d. %s\n", j + 1, quiz[i].options[j]);
        }

        printf("Enter your answer (1-4): ");
        scanf("%d", &user_answer);

        // Check if the user's answer is correct
        if (user_answer - 1 == quiz[i].correct_option) {
            printf("Correct!\n\n");
            score++;
        } else {
            printf("Incorrect. The correct answer was: %d. %s\n\n", 
                   quiz[i].correct_option + 1, quiz[i].options[quiz[i].correct_option]);
        }
    }

    printf("Quiz finished! You scored %d out of %d.\n", score, num_questions);

    return 0;
}
