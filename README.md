# Final Project: Password Checker 

A simple Python-based cybersecurity tool designed to evaluate password strength based on length, uppercase/lowercase letters, numbers, and special characters.

##  Python Code (`password_checker.py`)

```python
import re

def check_password_strength(password):
    score = 0
    feedback = []

    if len(password) >= 8:
        score += 1
    else:
        feedback.append("Password should be at least 8 characters long.")

    if re.search(r"[A-Z]", password):
        score += 1
    else:
        feedback.append("Add at least one uppercase letter.")

    if re.search(r"[a-z]", password):
        score += 1
    else:
        feedback.append("Add at least one lowercase letter.")

    if re.search(r"[0-9]", password):
        score += 1
    else:
        feedback.append("Add at least one number.")

    if re.search(r"[@$!%*?&]", password):
        score += 1
    else:
        feedback.append("Add at least one special character (e.g., @$!%*?&).")

    print("\n" + "=" * 40)
    print("      PASSWORD STRENGTH REPORT      ")
    print("=" * 40)
    
    if score == 5:
        print("Strength: STRONG! Your password is secure.")
    elif 3 <= score < 5:
        print("Strength: MODERATE. Consider adding more security elements.")
    else:
        print("Strength: WEAK! Your password is easy to hack.")

    if feedback:
        print("\nSuggestions to improve:")
        for item in feedback:
            print(f"- {item}")
    print("=" * 40)

if __name__ == "__main__":
    print("Welcome to the Python Password Strength Checker!")
    user_password = input("Enter a password to test: ")
    check_password_strength(user_password)
