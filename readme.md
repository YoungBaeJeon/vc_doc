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

#### id ####
VC 의 ID  


#### type ###
| Type name              | Type description                     | attribute name of credentialSubject  |
|------------------------|--------------------------------------|--------------------------------------|
| NameCredential         | 휴대폰 본인인증 이름                   | name |
| DateOfBirthCredential  | 휴대폰 본인인증 생년월일 | dateOfBirth |
| GenderCredential       |  휴대폰 본인인증 성별                | gender |
| NationalityCredential  | 휴대폰 본인인증 내국인/외국인 구분   | nationality |
| MobileNumberCredential | 휴대폰 본인인증 휴대폰번호           | mobileNumber |
| TelecomCredential      | 휴대폰 본인인증 통신사               | telecom |
| EmailCredential        | Email 인증 주소                      | email |
```
{
    "type":["VerifiableCredential", "NameCredential"]
}
```

#### credentialSubject ####
name, dateOfBirth, gender, nationality, mobileNumber, telecom, email
각 attribute 의 데이터 정의가 필요. (dateOfBirth, gender, nationality, telecom)  
```
{
    "credentialSubject":{
        "id":"did:meta:0x0000...4983",
        "name":"Jeon, Young-Bae"
    }
}
```

#### issuer ####
issuer(AA) 의 did
```
{
    "issuer":"did:meta:0x00000000..4930"
}
```

#### issuanceDate ####
발행일. 'yyyy-MM-ddTHH:mm:zzZ'
```
{
    "issuanceDate":"2010-01-01T19:73:24+09:00Z"
}
```
#### proof ####
- type : 서명 알고리즘
    ```
    "proof":{
        "type":"EcdsaSecp256k1Signature2019"
    }
    ```
- creator : 서명자의 DID
    ```
    "proof":{
        "creator":"did:meta:0x0000..88483"
    }
    ```
- created : 생성 일자. 'yyyy-MM-ddTHH:mm:zzZ'
    ```
    "proof":{
        "created":"2017-09-23T20:21:34Z"
    }
    ```
- nonce : replay attack 을 막기위한 난수값
    ```
    "proof":{
        "nonce":"2bbgh3dgjg2302d"
    }
    ```
- jws : signature
    ```
    "proof":{
        "jws:"jdau31..bj398ahd"
    }
    ```

###### proof signature ######
proof 는 JWT 를 사용하여 서명한다.  
[JWTs](https://w3c.github.io/vc-data-model/#jwt-encoding)  

JWT Hteader
```
{
    "alg":"ES256K", // Fixed ES256K
    "typ":"JWT",    // Fixed JWT
    "kid":"did:meta:0x9834...4893#ManagementKey#0x1843..4334#key-1"   // 서명자(AA)의 Key ID
}
```
JWT Payload
```
{
  "sub": "did:example:ebfeb1f712ebc6f1c276e12ec21",     // vc.credentialObject.id
  "iss": "https://example.com/keys/foo.jwk",            // issuer DID. vc.issuer or vp.holder
  "nbf": 1541493724,                                    // vc.issuanceData.  UNIX timestamp
  "exp": 1573029723,                                    // vc.expriationDate. UNIX timestamp
  "nonce": "660!6345FSer",                              // nonce
  "vc": {
    "@context": [
      "https://www.w3.org/2018/credentials/v1",
      "https://www.w3.org/2018/credentials/examples/v1"
    ],
    "type": ["VerifiableCredential", "UniversityDegreeCredential"],
    "credentialSubject": {
      "degree": {
        "type": "BachelorDegree",
        "name": "Bachelor of Science and Arts"
      }
    }
  }
}
```



#### Verifiable Credentials Library
- Java
    - [verifiable-credentials-java](https://github.com/TrustNetFI/verifiable-credentials-java). jsonld-ld-signature.
- Node
    - [vc-js](https://github.com/digitalbazaar/vc-js). jsonld-ld-signature
- Swift
    - none

#### Signature library
- Java
  - [ld-signatures-java](https://github.com/WebOfTrustInfo/ld-signatures-java)
