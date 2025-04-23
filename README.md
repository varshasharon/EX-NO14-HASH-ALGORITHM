# EX-NO14-HASH-ALGORITHM

## AIM:
To implement HASH ALGORITHM

## ALGORITHM:

1. Hash Algorithm is used to convert input data (message) into a fixed-size string, typically a hash value, which uniquely represents the original data.

2. Initialization:
   - Choose a hash function \( H \) (e.g., SHA-256, MD5, etc.).
   - The message \( M \) to be hashed is input.

3. Message Preprocessing:
   - Break the message \( M \) into fixed-size blocks. If necessary, pad the message to make it compatible with the block size required by the hash function.
   - For example, in SHA-256, the message is padded to ensure that its length is a multiple of 512 bits.

4. Hash Calculation:
   - Process the message block by block, applying the hash function \( H \) iteratively to produce an intermediate hash value.
   - For SHA-256, each block is processed through a series of logical operations, bitwise manipulations, and modular additions.

5. Output:
   - After all blocks are processed, the final hash value (digest) is produced, which is a fixed-size output (e.g., 256-bit for SHA-256).
   - The resulting hash is unique to the input message, meaning even a small change in the message will result in a completely different hash.

6. Security: The strength of the hash algorithm lies in its collision resistance, ensuring that it is computationally infeasible to find two different messages that produce the same hash value.


## Program:
```
#include <stdio.h>
#include <string.h>
#define MAX 100
void encrypt(char *plaintext, int shift, char *ciphertext) {
 int i;
 for (i = 0; plaintext[i] != '\0'; i++) {
 char ch = plaintext[i];
 if (ch >= 'A' && ch <= 'Z') {
 ciphertext[i] = (ch + shift - 'A') % 26 + 'A';
 } else if (ch >= 'a' && ch <= 'z') {
 ciphertext[i] = (ch + shift - 'a') % 26 + 'a';
 } else {
 ciphertext[i] = ch;
 }
 }
 ciphertext[i] = '\0';
}
void decrypt(char *ciphertext, int shift, char *plaintext) {
 int i;
 for (i = 0; ciphertext[i] != '\0'; i++) {
 char ch = ciphertext[i];
 if (ch >= 'A' && ch <= 'Z') {
 plaintext[i] = (ch - shift - 'A' + 26) % 26 + 'A';
 } else if (ch >= 'a' && ch <= 'z') {
 plaintext[i] = (ch - shift - 'a' + 26) % 26 + 'a';
 } else {
 plaintext[i] = ch;
 }
 }
 plaintext[i] = '\0';
}
int main() {
 printf("********** HASH (Encryption and Decryption) **********\n");
 char plaintext[MAX], ciphertext[MAX];
 int shift;
 printf("\nEnter the plaintext: ");
 fgets(plaintext, sizeof(plaintext), stdin);
 plaintext[strcspn(plaintext, "\n")] = 0;
 printf("\nEnter the shift value (1-25): ");
 scanf("%d", &shift);
 encrypt(plaintext, shift, ciphertext);
 printf("\nEncrypted text: %s\n", ciphertext);
 decrypt(ciphertext, shift, plaintext);
 printf("Decrypted text: %s\n", plaintext);
 return 0;
}
```

## Output:
![image](https://github.com/user-attachments/assets/20e82afe-287b-4c4f-8118-b40792416a10)

## Result:
The program is executed successfully.
