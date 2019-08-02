## JSON Web Algorithms

#### JWK Algorithms ####
[Reference](https://tools.ietf.org/html/rfc7518#section-6)

| kty           | Key type                        |
|---------------|---------------------------------|
| EC            | Elliptic Curve                  |
| RSA           | RSA                             |
| oct           | Octet sequcnec (symmetric keys) |


#### JWS Algorithms ####
[Reference](https://tools.ietf.org/html/rfc7518#section-3.1)

| alg           | signature or MAC algorithm                       | IETF Standard |
|---------------|--------------------------------------------------|---------------|
| HS256         | HMAC using SHA-256                               | O             |
| HS384         | HMAC using SHA-384                               | O             |
| HS512         | HMAC using SHA-512                               | O             |
| RS256         | RSASSA-PKCS1-v1_5 using SHA-156                  | O             |
| RS384         | RSASSA-PKCS1-v1_5 using SHA-384                  | O             |
| RS512         | RSASSA-PKCS1-v1_5 using SHA-512                  | O             |
| ES256         | ECDSA using P-256 and SHA-256                    | O             |
| ES384         | ECDSA using P-384 and SHA-384                    | O             |
| ES512         | ECDSA using P-521 and SHA-512                    | O             |
| PS256         | RSASSA-PSS using SHA-256 and MGF1 with SHA-256   | O             |
| PS384         | RSASSA-PSS using SHA-384 and MGF1 with SHA-384   | O             |
| PS512         | RSASSA-PSS using SHA-512 and MGF1 with SHA-512   | O             |
| none          | No digital signature or MAC performed            | O             |
| **ES256K**    | **ECDSA using P-256K1 (secp256k1) and SHA-256**  | X             |
| **ES256K-R**  | **Raw EC sign like bitcoin or ethereum**         | X             |

#### JWE Alogrithms ####

Key Management Algorithms  
[Reference](https://tools.ietf.org/html/rfc7518#section-4)

| alg                | Key Management Algorithm                                 |
|--------------------|----------------------------------------------------------|
| RSA1_5             | RSAES-PKCS1-v1_5                                         |
| RSA-OAEP           | RSAES OAEP                                               |
| RSA-OAEP-256       | RSAES OAEP using SHA-256 and MGF1 with SHA-256           |
| A128KW             | AES Wrap 128 bit                                         |
| A192KW             | AES Wrap 192 bit                                         |
| A256KW             | AES Wrap 256 bit                                         |
| dir                | direct symmetric key                                     |
| ECDH-ES            | ECDH Ephemeral static key agreement usgin concat KDF     |
| ECDH-ES+A128KW     | ECDH-ES usgin Concat KDF and A128KW                      |
| ECDH-ES+A192KW     | ECDH-ES usgin Concat KDF and A192KW                      |
| ECDH-ES+A256KW     | ECDH-ES usgin Concat KDF and A1256KW                     |
| A128GCMKW          | Key wrapping AES GCM 128-bit                             |
| A192GCMKW          | Key wrapping AES GCM 192-bit                             |
| A256GCMKW          | Key wrapping AES GCM 256-bit                             |
| PBES2-HS256+A128KW | PBES2 with HMAC SHA-256 and A128KW wrapping              |
| PBES2-HS384+A192KW | PBES2 with HMAC SHA-384 and A192KW wrapping              |
| PBES2-HS512+A256KW | PBES2 with HMAC SHA-512 and A256KW wrapping              |

Contents Encryption Algorithm  
[Reference](https://tools.ietf.org/html/rfc7518#section-5)

| enc           | Encryption algorithm      |
|---------------|---------------------------|
| A128CBC-HS256 | AES_128_CBC_HMAC_SHA_256  |
| A192CBC-HS384 | AES_192_CBC_HMAC_SHA_384  |
| A256CBC-HS512 | AES_256_CBC_HMAC_SHA_512  |
| A128GCM       | AES GCM 128-bit key       |
| A192GCM       | AES GCM 192-bit key       |
| A256GCM       | AES GCM 256-bit key       |


#### JOSE Library
- Java
    - [Nimbus-jose-jwt](https://bitbucket.org/connect2id/nimbus-jose-jwt). Supported secp256k1 (ECDSA).
    - [josej](https://bitbucket.org/b_c/jose4j). Not supported secp256k1.
- Node
    - [node-jose](https://github.com/cisco/node-jose). Not supported secp256k1.
    - [@panva/jose](https://github.com/panva/jose). Supported secp256k1 (ECDSA).
- Swift
    - [JOSESwift](https://github.com/airsidemobile/JOSESwift). Not supported secp256k1.


## Verifiable Credentials
[Reference](https://w3c.github.io/vc-data-model)  

#### Credential Type ###
| Type name | Type description    |
|-----------|---------------------|
|           |                     |

휴대폰본인인증에 대한 VC 가 아니라 각 항목에 대한 VC 가 생성되어야 함.  
Credential 이름에 휴대폰본인인증이라는 이름을 같이 표시해야 할듯.

#### Credential Subject ####
각 항목 이름 정의

#### Proofs ####
- External Proof
  - JSON Web Token
- Embedded Proof 
  - [Linked Data Signature](https://w3c-dvcg.github.io/ld-signatures)
  - [Linked Data Proofs]()
  
서명 방식은 동일하고 지원 항목이 좀 다름.  
초기에는 간단하게 JWT 쓰는 것이 좋을 것 같음.  

[비교](https://w3c.github.io/vc-imp-guide/#proofs)



#### Verifiable Credentials Library
- Java
    - [verifiable-credentials-java](https://github.com/TrustNetFI/verifiable-credentials-java). jsonld-ld-signature.
- Node
    - [vc-js](https://github.com/digitalbazaar/vc-js)
- Swift


#### Signature library
- Java
  - [ld-signatures-java](https://github.com/WebOfTrustInfo/ld-signatures-java)
