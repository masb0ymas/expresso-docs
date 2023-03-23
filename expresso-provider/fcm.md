# fcm

{% hint style="info" %}
FCM Provider from expresso-provider
{% endhint %}

Using commonjs

```javascript
const { FCM } = require('expresso-provider')
```

Using ES6

```javascript
import { FCM } from 'expresso-provider'
```

### Initialize FCM

```javascript
import { FCM } from 'expresso-provider'
import * as admin from 'firebase-admin'
import path from 'path'

const serviceAccountPath = path.resolve(
  `${process.cwd()}/public/gcp/fcm_serviceAccount.json`
)

export const fcmService = new FCM({
  options: { credential: admin.credential.cert(serviceAccountPath) },
})

fcmService.initialize()
```

### Using FCM

```javascript
import { fcmService } from 'config/fcm'

const payload = {
    'text': 'any value'
}

const dataFcm = await fcmService.sendToDevice({
    appName: 'My App',
    title: 'Your App Notif',
    deviceTokens: ['device_token_1', 'device_token_2'],
    message: 'Welcome to my App',
    type: 'Notif',
    data: JSON.stringify(payload),
})

console.log({ dataFcm })
```
