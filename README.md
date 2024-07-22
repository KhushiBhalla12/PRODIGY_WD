# PIXEL MANIPULATION FOR IMAGE
def encrypt(text, shift):
    result = ""
    # Loop through each character in the text
    for char in text:
        # Encrypt uppercase characters
        if char.isupper():
            result += chr((ord(char) + shift - 65) % 26 + 65)
        # Encrypt lowercase characters
        elif char.islower():
            result += chr((ord(char) + shift - 97) % 26 + 97)
        # If the character is not a letter, add it as it is
        else:
            result += char
    return result

def decrypt(text, shift):
    return encrypt(text, -shift)

def main():
    while True:
        # Prompt the user to choose the operation
        choice = input("Would you like to (E)ncrypt, (D)ecrypt, or (Q)uit? ").upper()
        if choice == 'Q':
            break
        elif choice not in ('E', 'D'):
            print("Invalid choice. Please enter E, D, or Q.")
            continue

        # Input the message
        message = input("Enter your message: ")
        
        # Input the shift value
        try:
            shift = int(input("Enter the shift value: "))
        except ValueError:
            print("Shift value must be an integer.")
            continue
        
        if choice == 'E':
            print("Encrypted message:", encrypt(message, shift))
        elif choice == 'D':
            print("Decrypted message:", decrypt(message, shift))

if __name__ == "__main__":
    main()

