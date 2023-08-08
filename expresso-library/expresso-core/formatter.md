# Formatter

{% hint style="info" %}
library formatter to simplify validate and format value
{% endhint %}

Using commonjs

```javascript
const { ms } = require('expresso-core')
```

Using ES6

```javascript
import { ms } from 'expresso-core'
```

***

### Format ms 1d ( 1 day )

```javascript
import { ms } from 'expresso-core'

const result = ms('1d')

console.log(result)

// output:
86400000
```

***

### format ms 5m ( 5 minute )

```javascript
import { ms } from 'expresso-core'

const result = ms('5m')

console.log(result)

// output:
300000
```

***

### isNumeric value

```javascript
import { isNumeric } from 'expresso-core'

const result = isNumeric('10')

console.log(result)

// output:
10
```

***

### Validate Number value

```javascript
import { validateNumber } from 'expresso-core'

const result = validateNumber('10')

console.log(result)

// output:
10

// Wrong Value
const wrongResult = validateNumber(false)

console.log(result)

// output:
0
```

***

### Validate Boolean value

```javascript
import { validateBoolean } from 'expresso-core'

const result = validateBoolean('true')

console.log(result)

// output:
true

// Wrong Result
const result = validateBoolean(null)

console.log(result)

// output:
false
```

***

### Validate Empty value

```javascript
import { validateEmpty } from 'expresso-core'

const result = validateEmpty('any value')

console.log(result)

// output:
'any value'

// Wrong Result
const result = validateEmpty(null)

console.log(result)

// output:
null
```
