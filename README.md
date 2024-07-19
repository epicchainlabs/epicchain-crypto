
# EpicChain Crypto Library

**Attention: This library is deprecated and no longer supported.**

For handling WIF (Wallet Import Format), key management, and RFC6979 signatures, please refer to the updated repositories and documentation:
- For Wallet Import Format (WIF) and key management, visit [EpicChain Crypto Key Management](https://pkg.go.dev/github.com/epicchain-dev/epic-go/pkg/crypto/keys).
- For RFC6979 signature generation and verification, refer to [EpicChain RFC6979](https://pkg.go.dev/github.com/epicchain-dev/rfc6979).
- For EpicChain-specific signatures using SHA-512 hashes, see [EpicChain SDK ECDSA](https://pkg.go.dev/github.com/epicchain-dev/epic-sdk-go/crypto/ecdsa).

The package you are referring to previously contained useful methods for working with cryptographic primitives used in EpicChain/EpicFS. Below are examples demonstrating how to perform common cryptographic operations with this library:

## Examples

### Simple Marshal / Unmarshal ECDSA Public Key (PK):

To convert an ECDSA public key to and from a byte slice:

```go
// Marshal the ECDSA public key into a slice of 33 bytes
data := crypto.MarshalPublicKey(&sk.PublicKey)

// Unmarshal the slice of 33 bytes back into an ECDSA public key
pk := crypto.UnmarshalPublicKey(data)
```

### Simple Marshal / Unmarshal ECDSA Private Key (SK):

To convert an ECDSA private key to and from a byte slice:

```go
// Marshal the ECDSA private key into a slice of 32 bytes
data := crypto.MarshalPrivateKey(&sk)

// Unmarshal the slice of 32 bytes back into an ECDSA private key, returning an error if something went wrong
newSk, err := crypto.UnmarshalPrivateKey(data)
```

### ECDSA Sign / Verify Bytes Using PK / SK

To sign and verify messages using an ECDSA private key (SK) and public key (PK):

```go
// Sign a message using the ECDSA private key, returning a signature as a slice of 65 bytes and an error if something went wrong
signature, err := crypto.Sign(sk, message)

// Verify the signature of a message using the ECDSA public key, returning an error if the public key is empty or if the signature is invalid
err := crypto.Verify(&sk.PublicKey, signature, message)
```

### RFC6979 Sign / Verify Bytes Using PK / SK

To sign and verify messages using RFC6979 for deterministic ECDSA signatures:

```go
// Sign a message using the ECDSA private key with RFC6979, returning a signature as a slice of 64 bytes and an error if something went wrong
signature, err := crypto.SignRFC6979(sk, message)

// Verify the signature of a message using the ECDSA public key with RFC6979, returning an error if the public key is empty or if the signature is invalid
err := crypto.VerifyRFC6979(&sk.PublicKey, signature, message)
```

### WIF Encode / Decode Private Key (SK)

To encode and decode private keys using Wallet Import Format (WIF):

```go
// Encode the ECDSA private key into a WIF string, returning an error if the key is invalid or empty
wif, err := crypto.WIFEncode(sk)

// Decode the WIF string back into an ECDSA private key, returning an error if the WIF string is invalid or cannot be decoded
skFromWIF, err := crypto.WIFDecode(wif)
```

### Load Private Key

To load a private key from various formats:

```go
// Load a private key from a WIF string
sk, err := crypto.LoadPrivateKey(wif_string)

// Load a private key from a hexadecimal string
sk, err := crypto.LoadPrivateKey(hex_string)

// Load a private key from a file path
sk, err := crypto.LoadPrivateKey(file_path)
```

The methods and examples provided here illustrate the essential cryptographic functions that were available in the EpicChain Crypto library. As this library is deprecated, please transition to the updated libraries and resources for continued support and development.

For further assistance or questions, refer to the documentation provided in the updated repositories or contact the EpicChain development team.