# Token

{% hint style="info" %}
handle jsonwebtoken for made easy
{% endhint %}

Using commonjs

```javascript
const { useToken } = require('expresso-hooks')
```

Using ES6

```javascript
import { useToken } from 'expresso-hooks'
```

***

### Generate Token

```typescript
const anyValue = { uuid: '3859acb9-c7b7-4273-b239-02dcf1e1fcb5' }
const anySecretKey = 'anyTestKey'

const data = useToken.generate({
  value: anyValue,
  secretKey: anySecretKey,
  expires: '1d',
})

console.log(data)

// output
{
  token: 'eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1aWQiOiIzODU5YWNiOS1jN2I3LTQyNzMtYjIzOS0wMmRjZjFlMWZjYjUiLCJpYXQiOjE2OTE0NjEwODcsImV4cCI6MTY5MTU0NzQ4N30.TUuhx8Eyf6Z8hBA3oY_S35aJ9E-PP1VaIznmocLkT9M',
  expiresIn: 86400
}
```

***

### Verify Token

```typescript
const anyValue = { uuid: '3859acb9-c7b7-4273-b239-02dcf1e1fcb5' }
const anySecretKey = 'anyTestKey'

const data = useToken.generate({
  value: anyValue,
  secretKey: anySecretKey,
  expires: '1d',
})

const result = useToken.verify({
  token: data.token,
  secretKey: anySecretKey,
})

console.log(result)

// output
{
  data: {
    uid: '3859acb9-c7b7-4273-b239-02dcf1e1fcb5',
    iat: 1691461087,
    exp: 1691547487
  },
  message: 'token is verify'
}
```
