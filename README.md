simplePGP
=========

This is a very simple and limited (but still fully functional) browser based PGP encryption/decryption utility. Most of the hard work is done by [OpenPGP.js](https://openpgpjs.org/).

To use simplePGP, you can run it live from the demo page, save it to your local machine and run it from there (see "Local Installation" below), or clone this repository.

Demo
====
You can it from any browser straight from GitHub just visit [https://skwirrel.github.io/simplePGP/pgp.html](https://skwirrel.github.io/simplePGP/pgp.html).

*N.B. The files you choose during the encryption/decryption process never leave your machine and are encrypted/decrypted by javascript running in the browser. The code runs entirely client-side.*

Using simplePGP
===============

Limitations
-----------
- This code simply does the encryption/decryption. It does not manage keys, keyrings, trust etc.
- It does not currently support signing or verifying signatures.
- It can only handle ascii-armoured files (both for keys and for encrypted data).
- It does not handle generation of keys yet - you will have to do that elsewhere (e.g. using https://gnupg.org/ )

Local Installation
------------------
For extra paranoia/convenience you might want to have your own local installation. That's fine and easy to do. simplePGP consists of just a single monolithic HTML file. Just [open the demo page](https://skwirrel.github.io/simplePGP/pgp.html) then right-click and select "Save as..." or whatever the equivalent is in your browser. Save the file `pgp.html` anywhere you want. When you want to use simplePGP just double click the file `pgp.html` you just saved and it should appear ready for use in your browser.

Suggested Use
-------------

### Storing Keys

Create a folder to store your keys - you could call it "keyring".
e.g.

    /keyring
          |---> /friend1_company.com.pub.key
          |---> /friend2_home.com.pub.key
          |---> /friend3_work.com.pub.key
          `---> /me_myaddress.com.priv.key

You can use whatever naming convention you like. All the keys must be "ascii armoured". That means if you load them into a text editor (e.g. notepad) they will start with....

    -----BEGIN PGP PUBLIC KEY BLOCK-----

and end with...

    -----END PGP PUBLIC KEY BLOCK-----

Obviously this will read "PRIVATE" instead of "PUBLIC" if you're looking at a private key.

You should store your private key somewhere where other's can't see it. It must also be protected with a strong passphrase (which you setup when you created the private key).

### Decrypting an Encrypted Message

**Step 1**

If the message is currently attached to an email you will need to save the encrypted message as a file. It doesn't matter what it is called but it must be "ascii armoured". That means if you load them into a text editor (e.g. notepad) they will start with....

    -----BEGIN PGP MESSAGE-----

and end with...

    -----END PGP MESSAGE-----

Typically these files will be created with a ".asc" extension. If it isn't ascii armoured you will have to ask the sender to send it again using the ascii armoured option.

**Step 2**

Bring up simplePGP in your browser for example by going to [https://skwirrel.github.io/simplePGP/pgp.html](https://skwirrel.github.io/simplePGP/pgp.html)

**Step 3**

Choose "Decrypt"

**Step 4**

Click the "Choose File" button to choose your private key file from the folder mentioned in the "Storing Keys" section above.

**Step 5**

A box will appear where you can enter the passphrase for your secret key

**Step 6**

Click the "Choose File" button to choose the file containing the encrypted data (the file you saved in Step 1 above).

**Step 7**

The file will be decrypted by your browser and the decrypted file automatically downloaded to your broweser's default downloads directory. The filename will be the name of the original file with any trailing ".asc" removed (if there was one).

### Encrypting a Message

**Step 1**

Bring up simplePGP in your browser for example by going to [https://skwirrel.github.io/simplePGP/pgp.html](https://skwirrel.github.io/simplePGP/pgp.html)

**Step 2**

Choose "Encrypt"

**Step 3**

Click the "Choose File" button to choose the public key file for the message recipient.

**Step 4**

Click the "Choose File" button to choose the file you want to encrypt.

**Step 5**

The file will be encrypted by your browser and the encrypted file automatically downloaded to your broweser's default downloads directory. The filename will be the name of the original file with ".asc" appended to the end.

