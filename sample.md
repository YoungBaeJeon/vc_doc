# Verifiable Credential Sample

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

##### JWT
```json
{
  "sub":"did:meta:0x11111111120",
  "iss":"did:meta:0x3489384932859420",
  "exp":1573724637,
  "iat":1565084637,
  "nonce":"0d8mf03",
  "vc":{
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiableCredential","NameCredential"],
    "credentialSubject":{"name":"mansud"}
  },
  "jti":"http://aa.metadium.com/credential/343"
}
```
