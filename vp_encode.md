# Verifiable Presentation encode/decode

## Encoding

##### Verifiable Credential JSON
```
{
  "@context":["https://w3id.org/credentials/v1"],
  "type":["VerifiablePresentation","TestPresentation"],
  "id":"http://aa.metadium.com/presentation/343",
  "holder":"did:meta:0x3489384932859420",
  "verifiableCredential":[
    "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
  ]
}
```

#### JWT. Use payload of JWS
- Move from vp.id to jwt.jti  
  JWT
  ```
  {
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
  VP
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiablePresentation","TestPresentation"],
    "holder":"did:meta:0x3489384932859420",
    "verifiableCredential":[
      "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
    ]
  }
  ```
- Move from vp.holder to jwt.iss  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
  VP
  ```
  {
    "@context":["https://w3id.org/credentials/v1"],
    "type":["VerifiablePresentation","TestPresentation"],
    "verifiableCredential":[
      "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
    ]
  }
  ```
- Move form vp to jwt.vp  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "vp":{
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ]
    },
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
- Add nonce. OPTION  
  JWT
  ```
  {
    "iss":"did:meta:0x3489384932859420",
    "vp":{
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ]
    },
    "nonce":"0d8mf03",
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```

##### Signed JWT
```
eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJpc3MiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAiLCJ2cCI6eyJAY29udGV4dCI6WyJodHRwczpcL1wvdzNpZC5vcmdcL2NyZWRlbnRpYWxzXC92MSJdLCJ0eXBlIjpbIlZlcmlmaWFibGVQcmVzZW50YXRpb24iLCJUZXN0UHJlc2VudGF0aW9uIl0sInZlcmlmaWFibGVDcmVkZW50aWFsIjpbImV5SnJhV1FpT2lKa2FXUTZiV1YwWVRvd2VETTBPRGt6T0RRNU16STROVGswTWpBamEyVjVNU0lzSW5SNWNDSTZJa3BYVkNJc0ltRnNaeUk2SWtWVE1qVTJTeUo5LmV5SnpkV0lpT2lKa2FXUTZiV1YwWVRvd2VERXhNVEV4TVRFeE1USXdJaXdpYVhOeklqb2laR2xrT20xbGRHRTZNSGd6TkRnNU16ZzBPVE15T0RVNU5ESXdJaXdpWlhod0lqb3hOVGN6TnpJek1UVTRMQ0pwWVhRaU9qRTFOalV3T0RNeE5UZ3NJbTV2Ym1ObElqb2lNR1E0YldZd015SXNJblpqSWpwN0lrQmpiMjUwWlhoMElqcGJJbWgwZEhCek9sd3ZYQzkzTTJsa0xtOXlaMXd2WTNKbFpHVnVkR2xoYkhOY0wzWXhJbDBzSW5SNWNHVWlPbHNpVm1WeWFXWnBZV0pzWlVOeVpXUmxiblJwWVd3aUxDSk9ZVzFsUTNKbFpHVnVkR2xoYkNKZExDSmpjbVZrWlc1MGFXRnNVM1ZpYW1WamRDSTZleUp1WVcxbElqb2liV0Z1YzNWa0luMTlMQ0pxZEdraU9pSm9kSFJ3T2x3dlhDOWhZUzV0WlhSaFpHbDFiUzVqYjIxY0wyTnlaV1JsYm5ScFlXeGNMek0wTXlKOS5BUUdMalFLeExzTEtPQ1htQjQwQzNFcFVBbDFQcHVnYVlwenktSkR2dEVBMW9ZRGpJUWpVdm56WnBCc0xaWVVFa2NUVkdTZktyUXNxbmRCQTZIdlRvZyIsImV5SnJhV1FpT2lKa2FXUTZiV1YwWVRvd2VETTBPRGt6T0RRNU16STROVGswTWpBamEyVjVNU0lzSW5SNWNDSTZJa3BYVkNJc0ltRnNaeUk2SWtWVE1qVTJTeUo5LmV5SnpkV0lpT2lKa2FXUTZiV1YwWVRvd2VERXhNVEV4TVRFeE1USXdJaXdpYVhOeklqb2laR2xrT20xbGRHRTZNSGd6TkRnNU16ZzBPVE15T0RVNU5ESXdJaXdpWlhod0lqb3hOVGN6TnpJek1qRXlMQ0pwWVhRaU9qRTFOalV3T0RNeU1USXNJbTV2Ym1ObElqb2lNR1E0YldZd015SXNJblpqSWpwN0lrQmpiMjUwWlhoMElqcGJJbWgwZEhCek9sd3ZYQzkzTTJsa0xtOXlaMXd2WTNKbFpHVnVkR2xoYkhOY0wzWXhJbDBzSW5SNWNHVWlPbHNpVm1WeWFXWnBZV0pzWlVOeVpXUmxiblJwWVd3aUxDSk9ZVzFsUTNKbFpHVnVkR2xoYkNKZExDSmpjbVZrWlc1MGFXRnNVM1ZpYW1WamRDSTZleUp1WVcxbElqb2liV0Z1YzNWa0luMTlMQ0pxZEdraU9pSm9kSFJ3T2x3dlhDOWhZUzV0WlhSaFpHbDFiUzVqYjIxY0wyTnlaV1JsYm5ScFlXeGNMek0wTXlKOS5rZkJLRnFral9oazl6Ym0xWGljbUhnVl9fNE9GNEs4d0xLYm9UaHlrdXpJclc1WHR1QVRROHpldDZ1cE1IV3RueXo5Y3IzQzdDNmZLbndsTlBMczNvdyJdfSwibm9uY2UiOiIwZDhtZjAzIiwianRpIjoiaHR0cDpcL1wvYWEubWV0YWRpdW0uY29tXC9wcmVzZW50YXRpb25cLzM0MyJ9.ZkFXCPUOvlUpXyADbXV_rKgZuV6GgSr998vGpKhHKQoUBhK2pSBIF4MOIRjePPOforbbxnrlfJGH7ZGZUYu3mQ
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
    "iss":"did:meta:0x3489384932859420",
    "vp":{
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ]
    },
    "nonce":"0d8mf03",
    "jti":"http://aa.metadium.com/credential/343"
  }
  ```
- Create VP
  - Create vp from jwt.vp
    ```
    {
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ]
    }
    ```
  - Add holder from jwt.iss
    ```
    {
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ],
      "holder":"did:meta:0x3489384932859420"
    }
    ```
  - Add id from jwt.jti
    ```
    {
      "@context":["https://w3id.org\/credentials/v1"],
      "type":["VerifiablePresentation","TestPresentation"],
      "verifiableCredential":[
        "eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMTU4LCJpYXQiOjE1NjUwODMxNTgsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.AQGLjQKxLsLKOCXmB40C3EpUAl1PpugaYpzy-JDvtEA1oYDjIQjUvnzZpBsLZYUEkcTVGSfKrQsqndBA6HvTog","eyJraWQiOiJkaWQ6bWV0YToweDM0ODkzODQ5MzI4NTk0MjAja2V5MSIsInR5cCI6IkpXVCIsImFsZyI6IkVTMjU2SyJ9.eyJzdWIiOiJkaWQ6bWV0YToweDExMTExMTExMTIwIiwiaXNzIjoiZGlkOm1ldGE6MHgzNDg5Mzg0OTMyODU5NDIwIiwiZXhwIjoxNTczNzIzMjEyLCJpYXQiOjE1NjUwODMyMTIsIm5vbmNlIjoiMGQ4bWYwMyIsInZjIjp7IkBjb250ZXh0IjpbImh0dHBzOlwvXC93M2lkLm9yZ1wvY3JlZGVudGlhbHNcL3YxIl0sInR5cGUiOlsiVmVyaWZpYWJsZUNyZWRlbnRpYWwiLCJOYW1lQ3JlZGVudGlhbCJdLCJjcmVkZW50aWFsU3ViamVjdCI6eyJuYW1lIjoibWFuc3VkIn19LCJqdGkiOiJodHRwOlwvXC9hYS5tZXRhZGl1bS5jb21cL2NyZWRlbnRpYWxcLzM0MyJ9.kfBKFqkj_hk9zbm1XicmHgV__4OF4K8wLKboThykuzIrW5XtuATQ8zet6upMHWtnyz9cr3C7C6fKnwlNPLs3ow"
      ],
      "holder":"did:meta:0x3489384932859420",
      "id":"http://aa.metadium.com/presentation/343"
    }
    ```



