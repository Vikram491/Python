# Python
import random
from string import ascii_lowercase

NUM_QUESTIONS_PER_QUIZ = 5
QUESTIONS = {
    "python is a interpreter language.": [
        "True",
        "False",
    ],
    "python is a compiled language True or False.": [
        "False.",
        "True.",
    ],
    "python is a open source language True or False.": [
        "False.",
        "True.",
    ],
    "python is a cross platform language True or False.": [
        "True.",
        "False.",
    ],
    "python runs on the chrome browser True or False.": [
        "False.",
        "True.",
    ],

}
num_questions = min(NUM_QUESTIONS_PER_QUIZ, len(QUESTIONS))
questions = random.sample(list(QUESTIONS.items()), k=num_questions)

num_correct = 0
for num, (question, alternatives) in enumerate(questions, start=1):
    print(f"\nQuestion {num}:")
    print(f"{question}?")
    correct_answer = alternatives[0]
    labeled_alternatives = dict(
        zip(ascii_lowercase, random.sample(alternatives, k=len(alternatives)))
    )
    for label, alternative in labeled_alternatives.items():
        print(f"  {label}) {alternative}")

    while (answer_label := input("\nChoice? ")) not in labeled_alternatives:
        print(f"Please answer one of {', '.join(labeled_alternatives)}")

    answer = labeled_alternatives[answer_label]
    if answer == correct_answer:
        num_correct += 1
        print("⭐ Correct! ⭐")
    else:
        print(f"The answer is {correct_answer!r}, not {answer!r}")

print(f"\nYou got {num_correct} correct out of {num} questions")
answer


