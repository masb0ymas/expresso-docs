# Currency

{% hint style="info" %}
Library currency to simplify nominal formatting
{% endhint %}

Using commonjs

```javascript
const { currency } = require('expresso-core')
```

Using ES6

```javascript
import { currency } from 'expresso-core'
```

***

### Format with national currency symbol

```javascript
import { currency } from 'expresso-core'

const result = currency.format({
  nominal: 125000,
  options: { locale: 'id-ID', currency: 'IDR' },
})

console.log(result)

// output :
'Rp 125.000'
```

***

### Format nominal

```javascript
import { currency } from 'expresso-core'

const result = currency.format({ nominal: 125000 })

console.log(result)

// output :
'125.000'
```
