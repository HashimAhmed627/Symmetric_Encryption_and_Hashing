# Symmetric Encryption and Hashing
## Overview
This project demonstrates the implementation of symmetric encryption and hashing techniques to secure files and validate their integrity. It focuses on encrypting and decrypting sensitive data using a symmetric encryption algorithm and generating hash values to ensure the integrity of files.
## Tasks Covered
- Encrypt and Decrypt Files Using Symmetric Encryption
- Generate and Validate File Hashes for Integrity
# 
### Creating Sample Text Files
![Creating Sample Text Files](https://github.com/user-attachments/assets/3bbb959e-66d3-4394-be85-1230b46eb7c9)
`echo 'desired text' > 'filename'`: This command is used to write content into new files
- `echo`: Outputs the text either to the screen or redirects to a file
- `desired text`: The text you want to write into the file
- `>`: This symbol is used to redirect the output of the command to a file
- `filename`: The file where the text will be written (it will create the file if it doesn’t already exist or overwrite it if it does)

After running the command, we can see that there are now three new files; *clear_text.txt, plain.txt, and sample.txt*
______________________________________________________________________________________________________________
### Encrypting a File 
![Encrypting a File (Symmetric)](https://github.com/user-attachments/assets/464e14af-2d8a-4444-8a78-08060eba2cd1)
`openssl aes-256-cbc -e -pbkdf2 -in sample.txt -out encrypted_sample.txt`: This command encrypts the contents of `sample.txt` using AES-256-CBC encryption with PBKDF2 derivation and writes the result to a new file, `encrypted_sample.txt`
- `openssl`: A command-line tool for cryptographic operations
- `aes-256-cbc`: This specifies the encryption algorithm (AES with a 256-bit key in CBC mode)
- `-e`: Indicates encryption mode
- `-pbkdf2`: Ensures a stronger key derivation function to enhance security
- `-in sample.txt`: Specifies the output file where the encrypted content will be saved

`rm sample.txt`: This deletes the original file (`sample.txt`) to protect its plaintext content 
- `rm`: Removes files or directories

`cat encrypted_sample.txt`: After displaying the newly encrypted file, the contents appear unreadable, indicating that the file is now secure
______________________________________________________________________________________________________________
### Decrypting a File
![Decrypting a File (Symmetric)](https://github.com/user-attachments/assets/df2b65c8-b3f6-4db8-9dad-f88ba2b935be)
`openssl aes-256-cbc -d -pbkdf2 -in encrypted_sample.txt -out decrypted_sample.txt`: This command decrypts the contents of `encrypted_sample.txt` using the AES-256-CBC algorithm with PBKDF2 derivation and writes the decrypted content to `decrypted_sample.txt`
- `-d`: Indicates decryption mode
- `-in encrypted_sample.txt`: Specifies the input file that is encrypted (`encrypted_sample.txt)
- `-out decrypted_sample.txt`: Specifies the output file where the decrypted content will be saved (`decrypted_sample.txt`)

`diff decrypted_sample.txt sample.txt`: I ran this command to check for any differences between the original file (`sample.txt`) and the decrypted file (`decrypted_sample.txt`). Since the command returned no output, it confirms that the files are identical, validating that the encryption and decryption processes were successful
______________________________________________________________________________________________________________
### Hashing Files
![Hashing Regular File and Encrypted File](https://github.com/user-attachments/assets/55dd2878-5985-4c7e-a4d2-2835fe4267b7)
`sha256sum plain.txt > hashed_plain.txt`: This command generates the SHA-256 hash of the original file (`plain.txt`) and saves it to a new file (`hashed_plain.txt`)
`sha256sum encrypted_sample.txt > hashed_encrypted_sample.txt`: This command generates the SHA-256 hash of the encrypted file (`encrypted_sample.txt`) and saves it to a new file (`hashed_encrypted_sample.txt`)
- `sha256sum`: This command computes the SHA-256 hash of a file. SHA-256 is a cryptographic hash function that generates a 256-bit hash value
- `plain.txt` & `encrypted_sample.txt`: Input files to be hashed
- `hashed_plain.txt` & `hashed_encrypted_sample.txt`: Output files that will store the corresponding hash values

After hashing the two files, we observe that their hash values are entirely different, making it significantly harder for anyone to infer the contents of the original files
__________________________________________________________________________________________________________________
### Validating File Integrity
![Validating File Integrity](https://github.com/user-attachments/assets/3b66fc14-3ae5-4872-b64b-62d641592430)

