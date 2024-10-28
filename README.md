# EX.-NO-1-D-IMPLEMENTATION-OF-VIGENERE-CIPHER

## AIM:
  To implement the Vigenere Cipher substitution technique using C program.
  
## ALGORITHM:
  STEP-1: Arrange the alphabets in row and column of a 26*26 matrix.
  
  STEP-2: Circulate the alphabets in each row to position left such that the first letter is attached to last.
 
  STEP-3: Repeat this process for all 26 rows and construct the final key matrix.
  
  STEP-4: The keyword and the plain text is read from the user.
  
  STEP-5: The characters in the keyword are repeated sequentially so as to match with that of the plain text.
  
  STEP-6: Pick the first letter of the plain text and that of the keyword as the row  indices and column indices respectively.
  
  STEP-7: The junction character where these two meet forms the cipher character.
  
  STEP-8: Repeat the above steps to generate the entire cipher text.
  
## PROGRAM:
~~~
#include <stdio.h>
#include <string.h>

void generateKey(const char* str, const char* key, char* newKey) {
    int strLen = strlen(str);
    int keyLen = strlen(key);
    int i, j;

    for(i = 0; i < strLen; i++) {
        newKey[i] = key[i % keyLen];
    }
    newKey[i] = '\0';  // Null-terminate the new key
}

void cipherText(const char* str, const char* key, char* cipher_text) {
    int strLen = strlen(str);
    for(int i = 0; i < strLen; i++) {
        char x = (str[i] + key[i]) % 26;
        x += 'A';
        cipher_text[i] = x;
    }
    cipher_text[strLen] = '\0';  // Null-terminate the ciphertext
}

void originalText(const char* cipher_text, const char* key, char* orig_text) {
    int strLen = strlen(cipher_text);
    for(int i = 0; i < strLen; i++) {
        char x = (cipher_text[i] - key[i] + 26) % 26;
        x += 'A';
        orig_text[i] = x;
    }
    orig_text[strLen] = '\0';  // Null-terminate the original text
}

int main() {
    char str[] = "LOKESH";
    char keyword[] = "HELLO";
    char key[100];
    char cipher_text[100];
    char orig_text[100];

    generateKey(str, keyword, key);
    cipherText(str, key, cipher_text);
    originalText(cipher_text, key, orig_text);

    printf("Ciphertext : %s\n", cipher_text);
    printf("Original/Decrypted Text : %s\n", orig_text);

    return 0;
}
~~~

## OUTPUT:
![Screenshot 2024-10-16 150159](https://github.com/user-attachments/assets/ec3520ee-5685-42f2-9013-8aafa44c748d)


## RESULT:
  Thus the Vigenere Cipher substitution technique had been implemented successfully.
