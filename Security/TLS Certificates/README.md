## :lock: TLS 

1. Symmetric Encryption :key:

     - Uses the same key for encryption and decryption
     - Since it uses the same key for encryption and decryption, the key has to be exchanged between the sender and the receiver, there is a risk of hacker getting access to the key and decrypting the data

2. Asymmetric Encryption :closed_lock_with_key:

     - Uses a pair of keys: Private key and Public key
     - Easy way to understand thid is considering private key as a key and public key as a public lock. Lock can be accessed by anyone but can only be unlocked by its key which should be kept private

3. To securely transfer the Symmetric key from client to server, we use Asymmetric encryption
   
      - We generate a public and private key on the server
       
             $ openssl genrsa -out my-bank.key 1024

             $ openssl genrsa -in my-bank.key -pubout > my-bank.pem
    
      - Now when the user tries to access the server using https, it gets the public key from the server. The hacker can also get access to this public key

      - Once the user receives the public key from the server,  the user's browser encrypts the symmetric key using this public key received from the server

      - Then when the client sends encrypted symmetric key to the server, the hacker gets access to this encrypted key as well. However, the hacker cannot decrypt it because he/she does not have the private key needed to decrypt the encrypted symmetric key

      - The server can decrypt the encrypted symmetric key as it has the private key on it
      
      - The symmetric key is now only available to the client and the server. They can now safely use the symmetric key to encrypt and decrypt data from each other

4. Even if we use the method in step 3, there is a possibility of hacker getting access to our data by creating a fake server that pretends to be the real one. Hence the server sends certificate along with the public key to prove  that the server is who it says it is
