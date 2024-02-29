#!/bin/bash

encrypt_file() {
    openssl enc -aes-256-cbc -salt -in "$1" -out "$2"
    echo "File encrypted successfully!"
}

decrypt_file() {
    openssl enc -d -aes-256-cbc -in "$1" -out "$2"
    echo "File decrypted successfully!"
}

if [ $# -lt 3 ]; then
    echo "Usage: $0 [encrypt|decrypt] <input_file> <output_file>"
    exit 1
fi

operation=$1
input_file=$2
output_file=$3

case "$operation" in
    encrypt) encrypt_file "$input_file" "$output_file" ;;
    decrypt) decrypt_file "$input_file" "$output_file" ;;
    *) echo "Invalid operation. Please choose 'encrypt' or 'decrypt'." >&2; exit 1 ;;
esac

exit 0
