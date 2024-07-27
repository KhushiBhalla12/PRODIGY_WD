#IMPLEMENT CAESAR CIPHER
def caesar_cipher(message, shift, mode):
    result = ""
    shift = shift % 26  # Ensure shift is within the range of 0-25
    if mode == "decrypt":
        shift = -shift
    for char in message:
        if char.isalpha():
            # Handle uppercase and lowercase letters separately
            offset = 65 if char.isupper() else 97
            # Shift character and wrap around alphabet if necessary
            new_char = chr((ord(char) + shift - offset) % 26 + offset)
            result += new_char
        else:
            # Non-alphabetic characters are added unchanged
            result += char
    return result

def main():
    print("Caesar Cipher Program")
    mode = input("Enter mode (encrypt/decrypt): ").strip().lower()
    if mode not in ["encrypt", "decrypt"]:
        print("Invalid mode. Please enter 'encrypt' or 'decrypt'.")
        return
    message = input("Enter the message: ")
    try:
        shift = int(input("Enter the shift value: "))
    except ValueError:
        print("Invalid shift value. Please enter a number.")
        return 
    result = caesar_cipher(message, shift, mode)
    print(f"Result: {result}")
if __name__ == "__main__":
    main()
