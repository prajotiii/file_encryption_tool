# file_encryption_tool
This project is a simple yet powerful file encryption tool built using Python. It leverages the cryptography library to provide secure encryption and decryption functionalities for files. This tool is particularly useful for anyone needing to protect sensitive data by encrypting files before storing or sharing them.
# File Encryption Tool

## Overview

This project is a simple yet powerful file encryption tool built using Python. It leverages the `cryptography` library to provide secure encryption and decryption functionalities for files. This tool is particularly useful for anyone needing to protect sensitive data by encrypting files before storing or sharing them.

## Features

- **Encrypt Files:** Securely encrypt any file to protect its contents.
- **Decrypt Files:** Easily decrypt previously encrypted files to access the original data.
- **Key Management:** Automatically generates and stores an encryption key for secure file encryption and decryption.

## Installation

1. **Clone the Repository:**
    ```bash
    git clone https://github.com/your-username/file-encryption-tool.git
    cd file-encryption-tool
    ```

2. **Install Dependencies:**
    Ensure you have Python installed. Then, install the required `cryptography` library:
    ```bash
    pip install cryptography
    ```

## Usage

1. **Generate Encryption Key:**
    Run the script to generate an encryption key. This key will be used for both encrypting and decrypting files.
    ```python
    from cryptography.fernet import Fernet

    def generate_key():
        """
        Generates a key and saves it into a file named `encryption_key.key`
        """
        key = Fernet.generate_key()
        with open("encryption_key.key", "wb") as key_file:
            key_file.write(key)

    # Generate the key
    generate_key()
    ```

2. **Encrypt a File:**
    Use the `encrypt_file` function to encrypt your desired file.
    ```python
    def load_key():
        """
        Loads the key named `encryption_key.key` from the current directory
        """
        return open("encryption_key.key", "rb").read()

    def encrypt_file(file_name):
        """
        Given a filename (str), it encrypts the file and writes it
        """
        key = load_key()
        fernet = Fernet(key)

        with open(file_name, "rb") as file:
            file_data = file.read()

        encrypted_data = fernet.encrypt(file_data)

        with open(file_name + ".encrypted", "wb") as file:
            file.write(encrypted_data)

    # Example usage
    encrypt_file("example.txt")
    ```

3. **Decrypt a File:**
    Use the `decrypt_file` function to decrypt your encrypted file.
    ```python
    def decrypt_file(encrypted_file_name):
        """
        Given a filename (str), it decrypts the file and writes it
        """
        key = load_key()
        fernet = Fernet(key)

        with open(encrypted_file_name, "rb") as file:
            encrypted_data = file.read()

        decrypted_data = fernet.decrypt(encrypted_data)

        with open(encrypted_file_name.replace(".encrypted", ""), "wb") as file:
            file.write(decrypted_data)

    # Example usage
    decrypt_file("example.txt.encrypted")
    ```

## License

This project is licensed under the MIT License. See the `LICENSE` file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request or open an issue.

## Acknowledgements

- [Cryptography Library](https://cryptography.io/): The Python library used for encryption and decryption.
