# Decrypt an encrypted message

# Scenario
In this scenario, all of the files in your home directory have been encrypted. You’ll need to use Linux commands to break the Caesar cipher and decrypt the files so that you can read the hidden messages they contain.

## Task 1.  Read the contents of a file

In this task, you need to explore the contents of your home directory and read the contents of a file to get further instructions.

1. Use the ```ls``` command to list the files in the current working directory.
   The command to complete this step:

    ```
    ls /home/analyst
    ```

    Two files, ```Q1.encrypted``` and ```README.txt```, and a subdirectory, ```caesar```, are listed:
    ```
    Q1.encrypted  README.txt caesar
    ```
    The ```README.txt``` file contains an important message with instructions you need to follow.

2. Use the ```cat``` command to list the contents of the ```README.txt``` file.
    The command to complete this step:
    ```
    cat README.txt
    ```
    This will display the following output:
    ```
    Hello,
    All of your data has been encrypted. To recover your data, you will need to solve a cipher. To get started look for a hidden file in the caesar subdirectory.
    ```
    The message in the ```README.txt``` file advises that the ```caesar``` subdirectory contains a hidden file.

## Output
<img width="1418" height="89" alt="Screenshot 2026-01-27 at 4 47 46 PM" src="https://github.com/user-attachments/assets/ab7a4498-1838-45c9-b194-54fbfeaed7c8" />

## Task 2.  Find a hidden file

In this task, you need to find a hidden file in your home directory and decrypt the Caesar cipher it contains. This task will enable you to complete the next task.

1. First, use the ```cd``` command to change to the ```caesar``` subdirectory of your home directory:
    ```
    cd caesar
    ```
2. Use the ```ls -a``` command to list all files, including hidden files, in your home directory.

    The command to complete this step:

    ```
    ls -a
    ```

   This will display the following output:
   ```
   .  ..  .leftShift3
   ```
   Hidden files in Linux can be identified by their name starting with a period (.)

3. Use the ```cat``` command to list the contents of the ```.leftShift3``` file.
    The command to complete this step:
    ```
   cat .leftShift3
    ```
    The message in the ```.leftShift3``` file appears to be scrambled. This is because the data has been encrypted using a Caesar cipher. This cipher can be solved by shifting each alphabet character to the left or right by a fixed number of spaces. In this example, the shift is three letters to the left. Thus "d" stands for "a", and "e" stands for "b".

4. You can decrypt the Caesar cipher in the .leftshift3 file by using the following command:
    ```
    cat .leftShift3 | tr "d-za-cD-ZA-C" "a-zA-Z"
    ```
    **Note:** The ```tr``` command translates text from one set of characters to another, using a mapping. The first parameter to the ```tr``` command represents the input set of characters, and the second represents the output set of characters. Hence, if you provide parameters “abcd” and “pqrs”, and the input string to the ```tr``` command is “ac”, the output string will be “pr".

   This will display the following output:
   ```
   In order to recover your files you will need to enter the following command:

    openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
   ```

   In this case, the command ```tr "d-za-cD-ZA-C" "a-zA-Z"``` translates all the lowercase and uppercase letters in the alphabet back to their original position. The first character set, indicated by ```"d-za-cD-ZA-C"```, is translated to the second character set, which is ```"a-zA-Z"```.

   **Note:** The output provides you with the command you need to solve the next task!
   You don’t need to copy the command revealed in the output. It will be provided in the next task.
5. Now, return to your home directory before completing the next task:
   ```
   cd ~
   ```
   
## Output
   <img width="751" height="218" alt="Screenshot 2026-01-27 at 5 00 34 PM" src="https://github.com/user-attachments/assets/c68b8c0e-5c98-4b24-8870-b0fd4ad159c3" />

## Task 3.  Decrypt a file

Now that you have solved the Caesar cipher, in this task you need to use the command revealed in .leftshift3 to decrypt a file and recover your data so you can read the message it contains.

1. Use the exact command revealed in the previous task to decrypt the encrypted file:
   ```
   openssl aes-256-cbc -pbkdf2 -a -d -in Q1.encrypted -out Q1.recovered -k ettubrute
   ```
   **Syntax break down:**

   In this instance, the ```openssl``` command reverses the encryption of the file with a secure symmetric cipher, as indicated by ```AES-256-CBC```. The ```-pbkdf2``` option is used to add extra security to the key, and ```-a``` indicates the desired encoding for the output. The ```-d``` indicates decrypting, while ```-in``` specifies the input file and ```-out``` specifies the output file. The ```-k``` specifies the password, which in this example is ```ettubrute```.

2. Use the ls command to list the contents of your current working directory again.

   The command to complete this step:
   ```
   ls
   ```
   The new file ```Q1.recovered``` in the directory listing is the decrypted file and contains a message.

3. Use the ```cat``` command to list the contents of the ```Q1.recovered``` file.
   The command to complete this step:
   ```
   cat Q1.recovered
   ```

   This will display the following output:
   ```
   If you are able to read this, then you have successfully decrypted the classic cipher text. You recovered the encryption key that was used to encrypt this file. Great work!
   ```

## Output

<img width="1427" height="113" alt="Screenshot 2026-01-27 at 5 11 38 PM" src="https://github.com/user-attachments/assets/15cb6ab7-2b8d-4739-a7d7-daef095d2c43" />

## Conclusion
Great work! You now have practical experience in using basic Linux Bash shell commands to

-  list hidden files,
-  decrypt a Caesar cipher, and
-  decrypt an encrypted file.

