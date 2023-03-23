# random string

{% hint style="info" %}
library random string to simplify generate unique string
{% endhint %}

Using commonjs

```javascript
const { randomString } = require('expresso-core')
```

Using ES6

```javascript
import { randomString } from 'expresso-core'
```

### Using Random String

#### Random string generate by default length 32

```javascript
import { randomString } from 'expresso-core'

const result = randomString.generate() // by default length 32

console.log(result)

// output :
'aq52PvnFrtvsX6rtA8MLj27xR2HcEJht'
```

#### Generate with length 10

```javascript
const result = randomString.generate(10)

console.log(result)

// output :
'aq52PvnFrt'
```

#### Generate with type **Numeric**

```javascript
const result = randomString.generate({
  type: 'numeric',
  length: 5,
})

console.log(result)

// output :
'72810'
```
