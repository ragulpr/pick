+++
title = "Encryption"
date =  2017-10-09T12:35:00-07:00
weight = 2
+++

## Encryption
The encryption section controls encryption for pick.

Currently supported encryption types include `openpgp`, `aes_gcm`, and `chachapoly`.

#### ChaChaPoly
```toml
type = "chachapoly"
[encryption.chachapoly]
# Specifies the key derivation function to use.
# Currently supported values: "pbkdf2", "scrypt".
keyderivation = "pbkdf2"
  # Settings for the "pbkdf2" Key-Derivation type
  [encryption.chachapoly.pbkdf2]
  # The hash function to use for PBKDF2.
  # Currently supported values: "sha512", "sha256".
  hash = "sha512"
  # The number of iterations used to derive the key from your password.
  iterations = 100000
  # Specifies the salt length (in bytes) for the PBKDF2.
  saltlen = 16
  # Settings for the "scrypt" key-derivation type
  [encryption.chachapoly.scrypt]
  n = 131072
  r = 8
  p = 1
  # Specifies the salt length (in bytes) for Scrypt.
  saltlen = 16
```

#### Open PGP
```toml
type = "openpgp"
[encryption.openpgp]
# The cipher to use, currently supported: "aes256", "aes128".
# The number after "aes" specifies the key length (in bits).
cipher = "aes256"
# s2kcount sets the number of iterations used to derive a key from your password.
# The more iterations, the longer it takes to convert your password to a key.
# This increases the time required for e.g. dictionary-attacks.
# Currently supported values: 1024-65011712 (inclusive).
# Not all values in the 1024-65011712 range are legal and if an illegal value is selected,
# the value is automatically rounded up to the nearest legal value.
s2kcount = 65011712
```

#### AES GCM
```toml
type = "aes_gcm"
[encryption.aes_gcm]
# Specifies the key length (in bytes) to use for AES.
# Currently supported values: 32, 24, 16 for 256bit, 192bit, 128bit respectively.
keylen = 32
# Specifies the key derivation function to use.
# Currently supported values: "pbkdf2", "scrypt".
keyderivation = "pbkdf2"
  # Settings for the "pbkdf2" Key-Derivation type
  [encryption.aes_gcm.pbkdf2]
  # The hash function to use for PBKDF2.
  # Currently supported values: "sha512", "sha256".
  hash = "sha512"
  # The number of iterations used to derive the key from your password.
  iterations = 100000
  # Specifies the salt length (in bytes) for the PBKDF2.
  saltlen = 16
  # Settings for the "scrypt" key-derivation type
  [encryption.aes_gcm.scrypt]
  n = 131072
  r = 8
  p = 1
  # Specifies the salt length (in bytes) for Scrypt.
  saltlen = 16
```
