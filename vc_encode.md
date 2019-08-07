# Verifiable Credential Encode/decode

## Encoding

##### Verifiable Credential JSON
```json
{
  "@context":["https://w3id.org/credentials/v1"],
  "type":["VerifiableCredential","NameCredential"],
  "id":"http://aa.metadium.com/credential/343",
  "issuer":"did:meta:0x3489384932859420",
  "issuanceDate":"2019-08-06T09:39:56Z",
  "expirationDate":"2019-11-14T09:39:56Z",
  "credentialSubject":{
    "id":"did:meta:0x11111111120",
    "name":"mansud"
  }
}
```

#### JWT. Use payload of JWS
- Move from vc.id to jwt.jti  
  JWT
  ```
  {
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
  VC
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "issuer":"did:meta:0x3489384932859420",
    "issuanceDate":"2019-08-06T09:39:56Z",
    "expirationDate":"2019-11-14T09:39:56Z",
    "credentialSubject":{
      "id":"did:meta:0x11111111120",
      "name":"mansud"
    }
  }
  ```
- Move from vc.issuer to jwt.iss  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
  VC
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "issuanceDate":"2019-08-06T09:39:56Z",
    "expirationDate":"2019-11-14T09:39:56Z",
    "credentialSubject":{
      "id":"did:meta:0x11111111120",
      "name":"mansud"
    }
  }
  ```
- Move from vc.issuanceDate to jwt.iat. convert value rfc3339 => unix timestamp  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "iat":1565084637,
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```  
  VC
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "expirationDate":"2019-11-14T09:39:56Z",
    "credentialSubject":{
      "id":"did:meta:0x11111111120",
      "name":"mansud"
    }
  }
  ```
- Move from vc.expirationDate to jwt.exp convert value rfc3339 => unix timestamp  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "exp":1573724637,
    "iat":1565084637,
    "jti":"http://aa.metadium.com/credential/343",
  }
  ```
  
  VC
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "credentialSubject":{
      "id":"did:meta:0x11111111120",
      "name":"mansud"
    }
  }
  ```
- Move from vc.credentialSubject.id to jwt.sub  
  JWT
  ```
  {
    "sub":"did:meta:0x11111111120",
    "iss":"did:meta:0x3489384932859420",
    "exp":1573724637,
    "iat":1565084637,
    "jti":"http://aa.metadium.com/credential/343",
  }
  ```
  
  VC
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "credentialSubject":{
      "name":"mansud"
    }
  }
  ```
- Move form vc to jwt.vc  
  JWT
  ```
  {
    "sub":"did:meta:0x11111111120",
    "iss":"did:meta:0x3489384932859420",
    "exp":1573724637,
    "iat":1565084637,
    "vc":{
      "@context":["https://w3id.org/credentials/v1"],
      "type":["VerifiableCredential","NameCredential"],
      "credentialSubject":{
        "name":"mansud"
      }
    },
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
- Add nonce. OPTION  
  JWT
  ```
  {
    "sub":"did:meta:0x11111111120",
    "iss":"did:meta:0x3489384932859420",
    "exp":1573724637,
    "iat":1565084637,
    "nonce":"0d8mf03",
    "vc":{
      "@context":["https://w3id.org/credentials/v1"],
      "type":["VerifiableCredential","NameCredential"],
      "credentialSubject":{
        "name":"mansud"
      }
    },
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```

##### Signed JWT
```
eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzgyNzE1LCJpYXQiOjE1NjUxNDI3MTUsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.VzcicZwRX5hzklcQXJFfp4abJ-M6DlbjszOEjf1eUKsWbRT8T-WhB2weq0i3sTj2Qs2xnY1SmsDwtKHoPI3Qhg
```
Header
```
{
  "kid":"did:meta:0x3489384932859420#key1",
  "typ":"JWT",
  "alg":"ES256K"
}
```

## Decoding
- JWTs Verify
- Get JWT
  ```
  {
    "sub":"did:meta:0x11111111120",
    "iss":"did:meta:0x3489384932859420",
    "exp":1573724637,
    "iat":1565084637,
    "nonce":"0d8mf03",
    "vc":{
      "@context":["https://w3id.org/credentials/v1"],
      "type":["VerifiableCredential","NameCredential"],
      "credentialSubject":{
        "name":"mansud"
      }
    },
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
- Create VC
  - Create vc from jwt.vc
    ```
      {
        "@context":["https://w3id.org/credentials/v1"],
        "type":["VerifiableCredential","NameCredential"],
        "credentialSubject":{
          "name":"mansud"
        }
      }
    ```
  - Add issuer from jwt.iss
    ```
      {
        "@context":["https://w3id.org/credentials/v1"],
        "type":["VerifiableCredential","NameCredential"],
        "credentialSubject":{
          "name":"mansud"
        },
        "issuer":"did:meta:0x3489384932859420"
      }
    ```
  - Add issuanceDate to jwt.iat. convert value timestamp => rfc3339
    ```
      {
        "@context":["https://w3id.org/credentials/v1"],
        "type":["VerifiableCredential","NameCredential"],
        "credentialSubject":{
          "name":"mansud"
        },
        "issuer":"did:meta:0x3489384932859420",
        "issuanceDate":1565084637
      }
    ```
  - Add expirationDate to jwt.exp. convert value timestamp => rfc3339
    ```
      {
        "@context":["https://w3id.org/credentials/v1"],
        "type":["VerifiableCredential","NameCredential"],
        "credentialSubject":{
          "name":"mansud"
        },
        "issuer":"did:meta:0x3489384932859420",
        "issuanceDate":1565084637,
        "expirationDate":1573724637
      }
    ```
  - Add credentialSubject.id to jwt.sub
      ```
      {
        "@context":["https://w3id.org/credentials/v1"],
        "type":["VerifiableCredential","NameCredential"],
        "credentialSubject":{
          "name":"mansud",
          "id":"did:meta:0x11111111120"
        },
        "issuer":"did:meta:0x3489384932859420",
        "issuanceDate":1565084637,
        "expirationDate":1573724637
      }
    ```


