# Login

icruiting currently uses AWS Cognito under the hood. Therefore logging in to icruiting is done by gaining a Bearer token from AWS Cognito.

For any clients use the following library: [AWS Amplify](https://docs.amplify.aws/lib/auth/getting-started/q/platform/js/)

For manual testing you can use the following curl command to gain an access token.

```bash
curl -X POST https://cognito-idp.eu-central-1.amazonaws.com/ \
    -H 'X-Amz-Target: AWSCognitoIdentityProviderService.InitiateAuth' \
    -H 'Content-Type: application/x-amz-json-1.1' \
    -d '{"AuthParameters": {"USERNAME": "", "PASSWORD":""}, "AuthFlow": "USER_PASSWORD_AUTH", "ClientId":""}'
```

_Note_ The used algorithm and, therefore, the length of the tokens might differ.

```json
{
  "AuthenticationResult": {
    "AccessToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9 eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRG9lIiwiaWF0IjoxNTE2MjM5MDIyfQ.SflKxwRJSMeKKF2QT4fwpMeJf36POk6yJV_adQssw5c",
    "ExpiresIn": 3600,
    "IdToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gQmVlIiwiaWF0IjoxNTE2MjM5MDIyfQ.67Zt5CsOQr_5u_DgnnQSN5WzCUZgNmA9_fJxrcqueCQ",
    "RefreshToken": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJzdWIiOiIxMjM0NTY3ODkwIiwibmFtZSI6IkpvaG4gRGVlIiwiaWF0IjoxNTE2MjM5MDIyfQ.wiL_VstOtjUkVMqecTNFVzkBtSYS5Er3i4DCC2vxtEQ",
    "TokenType": "Bearer"
  },
  "ChallengeParameters": {}
}
```

Use the `IdToken` in your Authorization Header.

src: [Stackoverflow](https://stackoverflow.com/questions/58833462/aws-cognito-authentication-curl-call-generate-token-without-cli-no-clien)
