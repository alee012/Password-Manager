# Password-Manager

A password manager built with Python and Tkinter. Developed for learning purposes. 

This project is a local desktop application that allows users to store passwords securely using cryptography.

Note: I only tested this with macOS, but in theory it should work with Windows. 

## Testing The Program

 1. Download and unzip PasswordManager.zip to somewhere. 
 2. Install `cryptography` library. You can use the command `pip install -r requirements.txt` or `pip install cryptography` to achieve this. 
 3. Open PasswordManager directory with an editor.
 4. Run `main.py`. You can use the command `python main.py` achieve this. 

## How It Works 

When the application starts, it checks for a file named verifier.bin. If this file is missing, the program enters a "First Run" mode, prompting the user to create a master password. This generates a random encryption salt and an encrypted verification string. If the file exists, the program requires the user to log in, validating the entered password by attempting to decrypt the verifier file; if decryption succeeds, access is granted. 

When you type your password to log in, the application does not use it directly as an encryption key. Instead, it combines your password with encryption salt. It processes this combination through a cryptographic algorithm called PBKDF2 to "derive" a 32-byte Master Key. This key is held in the RAM and is the actual tool used to lock and unlock the data. 

While websites and usernames are stored as searchable text, the actual passwords and their cryptographic nonces are stored as binary blobs. This makes sure that they are unreadable without the master key.
