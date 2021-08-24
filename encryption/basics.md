<h2>Symmetric cryptography</h2>
When there is one key to encrypt and decrypt. The key is shared with both ends. Symmetric cryptography doesn't address if someone could eavesdrop and wait for the key to be shared with the recieving end. 
<h2>Asymmetric cryptography (Public-key)</h2>
Each person in the conversation creates two keys, a public key and a private key. The two keys are connected and are actaully very large numbers with certain mathematical properties. If you encode a message using a person's public key, they can decode it using their matching private key. 
First, Party A's public key is sent to Party B. Once party B recieve's party A's public key they can encrypt their message to party B using that public key. Once party B recieves the encrypted message, they can decrypt using their private key.
We know that if you encrypt a message with a certain public key, it can only be decripted by the matching private key. But, the opposite is also true. If you encrypt a message with acertain private key, it can only be decrypted by its matching public key.
If a private key is used to encrypt a message, that means the sender is easily identifable because the message could have only been encrypted by one person. The person with the private key.
<h2>Man-in-the-middle attack</h2>
When someone intercepts your message to someone else. The attacker can alter the message and pass it along or choose to simply eavesdrop.
Public key cryptography lets you address man-in-the-middle attacks by providing ways to verify the recipient and sender's identities. This is done through fingerprint verification.
