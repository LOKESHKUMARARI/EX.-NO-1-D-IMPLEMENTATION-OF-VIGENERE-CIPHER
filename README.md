# EX.4-IMPLEMENTATION-OF-VIGENERE-CIPHER

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
#include <ctype.h>

void generateKey(const char *plaintext, const char *keyword, char *key) {
    int len = strlen(plaintext);
    int keyword_len = strlen(keyword);
    for (int i = 0; i < len; i++) {
        key[i] = keyword[i % keyword_len];
    }
    key[len] = '\0';
}

void encryptVigenere(const char *plaintext, const char *key, char *ciphertext) {
    int len = strlen(plaintext);
    for (int i = 0; i < len; i++) {
        ciphertext[i] = ((plaintext[i] - 'A') + (key[i] - 'A')) % 26 + 'A';
    }
    ciphertext[len] = '\0';
}

void decryptVigenere(const char *ciphertext, const char *key, char *decryptedtext) {
    int len = strlen(ciphertext);
    for (int i = 0; i < len; i++) {
        decryptedtext[i] = ((ciphertext[i] - 'A') - (key[i] - 'A') + 26) % 26 + 'A';
    }
    decryptedtext[len] = '\0';
}

int main() {
    char plaintext[128] = "LOKESH";
    char keyword[128] = "KEY";
    char key[128];
    char ciphertext[128];
    char decryptedtext[128];

    // Ensure plaintext is in uppercase
    for (int i = 0; plaintext[i]; i++) {
        plaintext[i] = toupper(plaintext[i]);
    }

    // Generate the repeating key to match the length of the plaintext
    generateKey(plaintext, keyword, key);

    printf("Plaintext: %s\n", plaintext);
    printf("Keyword: %s\n", keyword);
    printf("Generated Key: %s\n", key);

    // Encrypt the plaintext
    encryptVigenere(plaintext, key, ciphertext);
    printf("Encrypted text: %s\n", ciphertext);

    // Decrypt the ciphertext
    decryptVigenere(ciphertext, key, decryptedtext);
    printf("Decrypted text: %s\n", decryptedtext);

    return 0;
}

~~~

## OUTPUT:

![image](https://github.com/user-attachments/assets/5bafef3e-0d5c-4bf0-8cd9-d6ebee1a94d3)



## RESULT:
  Thus the Vigenere Cipher substitution technique had been implemented successfully.
