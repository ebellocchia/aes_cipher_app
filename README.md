# AES Cipher application

## Introduction

Simple application based on my [aes_cipher](https://github.com/ebellocchia/aes_cipher) library.

## Installation

Just install the [aes_cipher](https://github.com/ebellocchia/aes_cipher) library to run the application, refer to its instruction.

## Usage

Basic usage:

    python aes_cipher_app.py -m <enc:dec> -p <password1,password2,...> -i <input_files_or_folder> -o <output_folder> [-s <salt>] [-t <itr_num>] [-v] [-h]

Parameters description:

|Short name|Long name|Description|
|---|---|---|
|-m|--mode|Operational mode: *enc* for encrypting, *dec* for decrypting|
|-p|--password|Password used for encrypting/decrypting. It can be a single password or a list of passwords separated by a comma|
|-i|--input|Input to be encrypted/decrypted. It can be a single file, a list of files separated by a comma or a folder (in this case all files in the folder will be encrypted/decrypted)|
|-o|--output|Output folder where the encrypted/decrypted files will be saved|
|-s|--salt|Optional: custom salt for master key and IV derivation, otherwise the default salt "[]=?AeS_CiPhEr><()" will be used|
|-t|--iteration|Optional: number of iteration for algorithm, otherwise the default value 524288 will be used|
|-v|--verbose|Optional: enable verbose mode|
|-h|--help|Optional: print usage and exit|

**NOTE:** the password shall not contain spaces or commas (in this case it will be interpreted as multiple passwords)

## Examples

Encrypt a file one time with the given password and salt. If *input_file* is a folder, all the files inside the folder will be encrypted:

    python aes_cipher_app.py -m enc -p test_pwd -i input_file -o encrypted -s test_salt

Decrypt the previous file:

    python aes_cipher_app.py -m dec -p test_pwd -i encrypted -o decrypted -s test_salt

Encrypt multiple files one time with the given password and salt. If one of the input files is a directory, it will be discarded:

    python aes_cipher_app.py -m enc -p test_pwd -i input_file1,input_file2,input_file3 -o encrypted -s test_salt

Encrypt a file 3 times using 3 passwords with default salt and custom number of iteration:

    python aes_cipher_app.py -m enc -p test_pwd1,test_pwd2,test_pwd3 -t 131072 -i input_file -o encrypted

Decrypt the previous file:

    python aes_cipher_app.py -m dec -p test_pwd1,test_pwd2,test_pwd3 -t 131072 -i encrypted -o decrypted
