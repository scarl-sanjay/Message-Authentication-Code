# EX-NO 13 Message Authentication Code (MAC)

## AIM:
To write a program to implement Message Authentication Code (MAC). 
## ALGORITHM:
STEP-1: Input the plaintext message and symmetric key. STEP-2: Input the MAC value. STEP-3: Perform XOR encryption
STEP-4: Display the encrypted message
STEP-5: Perform XOR decryption
STEP-6: Display the decrypted message
## PROGRAM :
```
#include <stdio.h>
#include <string.h>

#define MAX_LEN 256 // Maximum length of the message

// Function to perform XOR encryption
void encrypt(const char *input, const char *key, char *output) {
    int len = strlen(input);
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len]; // XOR operation
    }
    output[len] = '\0'; // Null-terminate the output string
}

// Function to perform XOR decryption
void decrypt(const char *input, const char *key, char *output, int len) {
    int key_len = strlen(key);
    for (int i = 0; i < len; i++) {
        output[i] = input[i] ^ key[i % key_len]; // XOR operation
    }
    output[len] = '\0'; // Null-terminate the output string
}

int main() {
    char message[MAX_LEN];    // Plaintext message
    char key[MAX_LEN];        // Symmetric key
    char input_mac[3];        // MAC input from the user
    char encrypted[MAX_LEN];  // Encrypted message
    char decrypted[MAX_LEN];  // Decrypted message

    printf("\n **Simulation of MAC Algorithm**\n\n");
    printf(" DEVELOPED BY : SANJAY S\n");
    printf(" REG NO : 212223040184\n\n");

    // Get plaintext message from the user
    printf("Enter the plaintext message: ");
    fgets(message, MAX_LEN, stdin);
    message[strcspn(message, "\n")] = 0; // Remove newline character

    // Get symmetric key from the user
    printf("Enter the symmetric key: ");
    fgets(key, MAX_LEN, stdin);
    key[strcspn(key, "\n")] = 0; // Remove newline character

    // Get MAC value from the user
    printf("Enter the MAC value (in hex format): ");
    scanf("%2s", input_mac); // Read the MAC input from the user

    // Perform encryption
    encrypt(message, key, encrypted);
    int encrypted_length = strlen(message);

    // Print encrypted message in hexadecimal format (raw bytes)
    printf("Encrypted message (raw bytes): ");
    for (int i = 0; i < encrypted_length; i++) {
        printf("%02x ", (unsigned char)encrypted[i]);
    }
    printf("\n");

    // Perform decryption
    decrypt(encrypted, key, decrypted, encrypted_length); // Pass the length of the encrypted message
    printf("Decrypted message: %s\n", decrypted);

    return 0;
}
```

## OUTPUT :
![image](https://github.com/user-attachments/assets/4adadadf-e162-4906-ad0b-bf82d226050f)

## RESULT :
Thus the Message Authentication Code (MAC) had been implemented sucessfully.
