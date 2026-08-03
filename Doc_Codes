"""
Password Generator
------------------
Generates strong, random passwords using letters, numbers, and symbols.
Lets the user choose the password length and save generated passwords
to a text file for later reference.
"""

import random
import string
import os

OUTPUT_FILE = "generated_passwords.txt"


def get_password_length():
    """Ask the user for a password length, validating the input."""
    while True:
        raw = input("Enter desired password length (minimum 4): ").strip()
        if raw.isdigit() and int(raw) >= 4:
            return int(raw)
        print("Please enter a whole number that is 4 or greater.")


def generate_password(length):
    """Generate a random password containing letters, numbers, and symbols."""
    letters = string.ascii_letters      # a-z, A-Z
    numbers = string.digits             # 0-9
    symbols = string.punctuation        # !@#$%^&* etc.

    all_characters = letters + numbers + symbols

    # Guarantee at least one character from each category for strength.
    password_chars = [
        random.choice(letters),
        random.choice(numbers),
        random.choice(symbols),
    ]

    # Fill the rest of the password length with random characters.
    password_chars += [
        random.choice(all_characters) for _ in range(length - len(password_chars))
    ]

    # Shuffle so the guaranteed characters aren't always in the same position.
    random.shuffle(password_chars)

    return "".join(password_chars)


def save_password(password):
    """Append the generated password to a text file."""
    file_path = os.path.join(os.getcwd(), OUTPUT_FILE)
    with open(file_path, "a", encoding="utf-8") as file:
        file.write(password + "\n")
    return file_path


def main():
    print("=" * 40)
    print("        STRONG PASSWORD GENERATOR")
    print("=" * 40)

    while True:
        length = get_password_length()
        password = generate_password(length)

        print("\nGenerated Password:")
        print(f"  {password}\n")

        save_choice = input("Save this password to a file? (y/n): ").strip().lower()
        if save_choice == "y":
            path = save_password(password)
            print(f"Password saved to: {path}\n")

        again = input("Generate another password? (y/n): ").strip().lower()
        if again != "y":
            print("\nGoodbye! Stay secure.")
            break


if __name__ == "__main__":
    main()
