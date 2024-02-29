# bash-script-to-automate-encryption-and-decryption-using-openssl
#!/bin/bash

# Define the input file
input_file="example.txt"

# Define the recipient's email address
recipient_email="recipient@example.com"

# Encrypt the file
echo "Encrypting the file..."
gpg --output "$input_file.gpg" --recipient "$recipient_email" --encrypt "$input_file"
echo "File encrypted successfully."

# Decrypt the file
echo "Decrypting the file..."
gpg --output "${input_file}_decrypted.txt" --decrypt "$input_file.gpg"
echo "File decrypted successfully."
