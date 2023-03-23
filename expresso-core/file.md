# file

{% hint style="info" %}
library file to simplify using filesystem
{% endhint %}

Using commonjs

```javascript
const { createDirNotExist } = require('expresso-core')
```

Using ES6

```javascript
import { createDirNotExist } from 'expresso-core'
```

#### Using create dir not exist

```javascript
import { createDirNotExist } from 'expresso-core'

const dir = `${process.cwd()}/public/temp`

createDirNotExist(dir)
```

#### Using read html file

```javascript
import { createDirNotExist } from 'expresso-core'

const filePath = path.resolve(`${process.cwd()}/public/output/test.html`)

const content = await readHTMLFile(filePath)

console.log(content)

// output:
// file buffer
```

#### Using delete file

```javascript
import { createDirNotExist } from 'expresso-core'

const filePath = path.resolve(`${process.cwd()}/public/output/test.txt`)

deleteFile(filePath)
```
