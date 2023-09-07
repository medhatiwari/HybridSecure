# File Storage Using Hybrid Cryptography


## Backend 
### Python

## Frontend
### HTML5, CSS3, Javascript

<hr>

<br>

## About 
This is a local file encryption platform designed to provide robust security and privacy for sensitive files.


#### Why to use it?
After the encryption process, users gain enhanced data security and control over their files. The encrypted files are protected against unauthorized access, ensuring the confidentiality of sensitive information. It can be used for:

*Secure Storage*: Encrypted files can be stored in various locations, including local storage, cloud services, or external devices, without the fear of data exposure in case of unauthorized access.

*Data Transfer*: Encrypted files can be safely transferred over networks or shared with others. Even if intercepted, the encrypted content remains indecipherable without the appropriate decryption keys.

*Backup*: Encrypted files can be included in backup routines, providing an added layer of security during data backup processes.

*Cloud Services*: Encrypted files can be uploaded to cloud storage services, enhancing data protection even when stored remotely.

*Collaboration*: Encrypted files can be shared with authorized collaborators. Only those with the necessary decryption keys can access the original content.


It is like a digital vault for your important files, ensuring they stay safe and private. Imagine it as a combination of a lock and a secret code. First, we divide big files into smaller parts, sort of like putting a puzzle into pieces. Then, we lock each piece using a special code that only you and your recipient know. This special code is like your personal key. Later, when you want to see your files again, we use your key to unlock and put all the puzzle pieces back together exactly as they were. 
<hr>
<br>

# Installation

Step 1: Install Requirements</br>
`pip install -r requirements.txt`</br>

Step 2: Run the application</br>
`python3 app.py` or try `python app.py`</br>

Step 3: Visit the localhost on your browser</br>


<hr>

### Encrypter.py
AESAlgoRotated, ChaChaAlgo, AESGCMAlgo, and AESCCMAlgo are all cryptographic algorithms that are used for the encryption and decryption of data. 

AESAlgoRotated is a variant of the Advanced Encryption Standard (AES) algorithm. It is an efficient encryption algorithm widely used for bulk data encryption. The AESAlgoRotated function in the code snippet rotates the encryption algorithm used for each file in a round-robin manner. This enhances security by mitigating vulnerabilities associated with using a single encryption method. The round-robin method creates a diverse encryption environment, making it more challenging for an attacker to break the encryption.

ChaChaAlgo is a stream cipher algorithm that generates a key stream of pseudorandom bits. These bits are XOR-ed with the plaintext to produce ciphertext. The ChaChaAlgo function in the Python code snippet encrypts the data using this algorithm. ChaChaAlgo is known for its speed and security, making it an excellent choice for applications that require fast encryption.

AESGCMAlgo is an authenticated encryption with associated data (AEAD) algorithm. It is a widely used encryption algorithm that provides both confidentiality and authenticity. The AESGCMAlgo function in the Python code snippet uses this algorithm to encrypt the data. The authenticity feature of AESGCMAlgo ensures that the encrypted data is not modified during transmission.

AESCCMAlgo is a mode of operation for AES that provides both confidentiality and authenticity. It is similar to AESGCMAlgo but uses a different method for generating the authentication tag. The AESCCMAlgo function in the Python code snippet uses this algorithm to encrypt the data.

These cryptographic algorithms are used in the encrypter function to encrypt different parts of the data.
<hr>

### Decryptor.py
The symmetric keys are extracted. These keys correspond to different encryption algorithms used during encryption. For each encrypted file fragment, the corresponding decryption algorithm is determined based on metadata or patterns established during encryption.

The specific decryption algorithm is selected, and the decrypted symmetric key associated with that algorithm is used. The AESAlgoRotated, ChaChaAlgo, AESGCMAlgo, and AESCCMAlgo functions are called based on the algorithm identified for each file fragment. These functions decrypt the encrypted file content using the appropriate decryption algorithm and the decrypted symmetric key. The decrypted content is then written to individual files in the "files" directory.

Finally, the individual fragments are reassembled in the correct order to recreate the original file. This process involves combining the split files into a single file in the correct order. The restored file is now available for download or further use.

<hr>

### Divider.py
To split the file, the function sets a maximum chapter size of 1 MB and a memory buffer size of 50 GB. The maximum chapter size determines the size of each file chapter, while the memory buffer size determines how much data can be read from the original file at a time. These values were chosen to optimize the speed and efficiency of the file-splitting process.

After setting these parameters, the function reads a file located in the "uploads" folder. The location of the file is determined by using the "list_dir" function from the "tools" module to list all files in the "uploads" folder and selecting the first file in the list.

The function then splits the file into chapters, with each chapter being written to a separate file in the "files" folder. To achieve this, the function uses a while loop to iterate through the original file, reading data in chunks and writing each chunk to a separate file. The loop continues until the entire file has been read and split into chapters.

In addition to splitting the file, the function also writes metadata about the original file to a file called "meta_data.txt" in the "raw_data" folder. This metadata includes the original file name and the number of chapters created.

The original file name is obtained by splitting the full file path and selecting the last element of the resulting list. The number of chapters created is tracked using a counter variable called "chapters", which is incremented each time a new chapter is created.<hr>

### Restore.py
The "restore" function uses various functions from the "tools" module to automate the file restoration process. The first step in the process is to empty the 'restored_file' folder using the "empty_folder" function. This ensures that the folder is empty and ready to receive the restored file.

Next, the function reads metadata from a file called 'meta_data.txt' using the "open" function and the "read" method. The metadata contains information about the original file, including the file name and the number of chapters created when the file was split. The metadata is stored in a list called "meta_info".

After reading the metadata, the function creates a file path for the restored file using the original file name obtained from the metadata. The file path is constructed by concatenating the string 'restored_file/' with the original file name obtained from the metadata.

Once the file path has been created, the function reads binary data from a list of files in the 'files' folder. The list of files is obtained using the "list_dir" function from the "tools" module. The function sorts the list of files alphabetically using the "sorted" function to ensure that the file chapters are read in the correct order.

The function then uses a nested "with" statement to open each file in the list and read its binary data. The binary data is read using the "read" method, which reads the entire contents of the file at once. The binary data is then written to the new file at the specified file path using the "write" method. The "write" method writes the binary data to the file in a single step.

Once all the file chapters have been read and written to the new file, the 'files' folder is emptied using the "empty_folder" function from the "tools" module. This ensures that the folder is empty and ready to be used for future file restorations.





![Home](image.png)





