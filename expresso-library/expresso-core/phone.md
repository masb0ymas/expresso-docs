# Phone

{% hint style="info" %}
format phonenumber with international phone & whatsapp
{% endhint %}

Using commonjs

```javascript
const { Phonenumber } = require('expresso-core')
```

Using ES6

```javascript
import { Phonenumber } from 'expresso-core'
```

***

### Format Phone with international format

```typescript
const phone = new Phonenumber({ country: 'ID' })

const myPhone = '081234567890'
const newPhone = phone.format(myPhone)

console.log(newPhone)

// output
+6281234567890
```

***

### Format phone for Whatsapp

```typescript
const phone = new Phonenumber({ country: 'ID' })

const myPhone = '081234567890'
const newPhone = phone.formatWhatsapp(myPhone)

console.log(newPhone)

// output
6281234567890@c.us
```

***

### Format hide phone number

```typescript
const phone = new Phonenumber({ country: 'ID' })

const myPhone = '081234567890'
const newPhone = phone.hidePhone(myPhone)

console.log(newPhone)

// output
+6281234***890
```
