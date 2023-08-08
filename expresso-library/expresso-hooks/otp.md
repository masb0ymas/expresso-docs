# OTP

{% hint style="info" %}
handle one time password made easier
{% endhint %}

Using commonjs

```javascript
const { useOTP } = require('expresso-hooks')
```

Using ES6

```javascript
import { useOTP } from 'expresso-hooks'
```

***

### Hash OTP

```typescript
const otp = new useOTP()

const anyPhone = '081234567890'
const anyOTP = '123456'
const anySecretKey = '1234567890abcdef'

const payload = JSON.stringify({ phone: anyPhone, otp: anyOTP })

const data = otp.hashOTP(payload, {
  expires: '1d',
  secretKey: anySecretKey,
})

console.log(data)

// output
439f8f1555a9266fbad880c45b6262216a94c8ac8e2def2468cd423323e7ad3c.1691548132497
```

***

### Verify OTP

```javascript
const otp = new useOTP()

const anyPhone = '081234567890'
const anyOTP = '123456'
const anySecretKey = '1234567890abcdef'

const payload = JSON.stringify({ phone: anyPhone, otp: anyOTP })

const hashOTP = otp.hashOTP(payload, {
  expires: '1d',
  secretKey: anySecretKey,
})

const verifyHash = otp.verifyHash(payload, hashOTP, {
  secretKey: anySecretKey,
})

console.log(verifyHash)

// output
true
```
