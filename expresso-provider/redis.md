# redis

{% hint style="info" %}
Redis Provider for expressjs
{% endhint %}

Using commonjs

```javascript
const { Redis } = require('expresso-provider')
```

Using ES6

```javascript
import { Redis } from 'expresso-provider'
```

### Initialize Redis

```javascript
import { Redis } from 'expresso-provider'

export const redisService = new Redis({
  host: '127.0.0.1',
  port: 6379,
  password: 'your_password',
})
```

### Using Redis

```javascript
import { redisService } from 'config/redis'
import { ms } from 'expresso-core'

const keyRedis = 'your_key'
const storeRedis = {
  'text': 'any value'
}
const expires = ms('10m')

// Set Redis
await redisService.set(keyRedis, JSON.stringify(storeRedis), {
  timeout: expires,
})

// Get Redis
const getStore = redisService.get(keyRedis)
```
