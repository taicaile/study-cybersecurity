# Security

```bash
# encryption
openssl enc -aes-128-cbc -in temp.txt -K ABCDEF12345 -iv ABCDEF > cipher.txt

# hexdump
xxd cipher.txt

# decryption
openssl enc -d -aes-128-cbc -in cipher.txt -K ABCDEF12345 -iv ABCDEF > decrypt.md
```

## Digital Signature

A unique signature attached/appended to file.

Generating the hash,

```bash
# generating hash
md5sum temp.txt
```

Generating digital signature,

```bash
sha1sum temp.txt | cut -d ' ' -f 1 > hash1
openssl enc -aes-128-cbc -in hash1 -K ABCDEF12345 -iv ABCDEF > signature.bin
```

Verifying digital signature,

```bash
# sha1sum Plaintext.txt | cut -d ' ' -f 1 > hash_1
openssl enc -d -aes-128-cbc -in signature.bin -K ABCDEF12345 -iv ABCDEF > hash_2
```
