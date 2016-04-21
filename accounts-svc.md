# Ocean - Accounts Service

The Accounts Service is intented to be the single source of truth for users registered with Ocean. 

Users will sign in with Github to enable:
* Frictionless verification of emails (Github reports if verified)
* Importing SSH public keys (maybe future)

### Entity Types

Account object

```
{
  "id": uuid,
  "username": string
}
```

AccountEmail object

```
{
  "id": uuid,
  "accountId": uuid,
  "email": string
}
```

GithubIdentifier object

```
{
  "id": uuid,
  "accountId": uuid,
  "githubId": int
```

## Accounts API

### Create Account

**POST /account**

```
X-Request-ID: dad9de9d-0fbc-400a-9f1f-2d9d1d9af686
{
  "username": "bobmarley"
}
```

Response:

```
201 CREATED
X-Request-ID: dad9de9d-0fbc-400a-9f1f-2d9d1d9af686
{
  "id": "fa496c42-6100-4838-9774-6683b3688cd2",
  "username": "bobmarley"
}
```

**GET /accounts/{:id}**

Response:

```
200 OK
{
  "id": "fa496c42-6100-4838-9774-6683b3688cd2",
  "username": "bobmarley"
}
```

**GET /accounts?username={:username}**

Response:

```
200 OK
{
  "id": "fa496c42-6100-4838-9774-6683b3688cd2",
  "username": "bobmarley"
}
```

**POST /github-identifiers**

```
{
  "accountId": "fa496c42-6100-4838-9774-6683b3688cd2",
  "githubId": 11368271
}
```

Response:

```
201 CREATED
{
  "id": "6b5dd49e-2102-45bf-b1d1-762cf3ca9d47",
  "accountId": "fa496c42-6100-4838-9774-6683b3688cd2",
  "githubId": "11368271"
}
```

**GET /github-identifiers?githubId={:githubId}**

Response:

```
200 OK
{
  "id": "6b5dd49e-2102-45bf-b1d1-762cf3ca9d47",
  "accountId": "fa496c42-6100-4838-9774-6683b3688cd2",
  "githubId": "11368271"
}
```
