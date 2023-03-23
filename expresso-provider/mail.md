# mail

{% hint style="info" %}
Mail Provider from expresso-provider
{% endhint %}

Using commonjs

```javascript
const { Mail } = require('expresso-provider')
```

Using ES6

```javascript
import { Mail } from 'expresso-provider'
```

### Initialize Mail

```javascript
import { Mail } from 'expresso-provider'

export const mailService = new Mail({
  appName: 'My App',
  driver: 'smtp',
  host: 'smtp.mailtrap.io',
  port: 2525,
  username: 'noreply@your_company.com',
  password: 'your_password',
})

mailService.initialize()
```

### Send Mail

```javascript
import { readHTMLFile } from 'expresso-core'
import { mailService } from 'config/mail'
import Handlebars from 'handlebars'

const filePath = '/your_path/template/emailRegistration.html'

const html = readHTMLFile(filePath)
const template = Handlebars.compile(html)

const mailTo = 'your_client@company.com'
const subject = 'Account Registration'
const htmlToSend = template(data)

mailService.send(mailTo, subject, htmlToSend)
```
