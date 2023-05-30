# ⚓ expresso-hooks

{% hint style="info" %}
Hooks library for expresso
{% endhint %}

## Install expresso-hooks

Using NPM

```bash
npm install --save expresso-hooks
```

Using Yarn

```bash
yarn add expresso-hooks
```

Using PNPM

```bash
pnpm add expresso-hooks
```

### Using Multer Middleware

{% embed url="https://www.npmjs.com/package/multer" %}
multer middleware
{% endembed %}

Using commonjs

```javascript
const { useMulter } = require('expresso-hooks')
```

Using ES6

```javascript
import { useMulter } from 'expresso-hooks'
```

#### Using useMulter full feature expresso starter backend

```javascript
import { useMulter } from 'expresso-hooks'
import _ from 'lodash'
import route from 'routes/v1'

// multer config
const uploadFile = useMulter({
  dest: 'public/uploads',
}).fields([{ name: 'fileUpload', maxCount: 1 }])

// set multer from req.file to req.body
const setFileToBody = asyncHandler(async function setFileToBody(
  req: Request,
  res,
  next: NextFunction
) {
  const fileUpload = req.pickSingleFieldMulter(['fileUpload'])

  req.setBody(fileUpload)
  next()
})

// parse to endpoint API
route.post(
  '/upload',
  uploadFile,
  setFileToBody,
  async function postUpload(req: Request, res: Response) {
    const formData = req.getBody()

    const fieldUpload = _.get(formData, 'fileUpload', {}) as FileAttributes

    console.log(fieldUpload)
  }
)

```

#### Using useMulter for simple expressjs

```javascript
import { useMulter } from 'expresso-hooks'
import _ from 'lodash'
import route from 'routes/v1'

// multer config
const uploadFile = useMulter({
  dest: 'public/uploads',
}).fields([{ name: 'fileUpload', maxCount: 1 }])

// parse to endpoint API
route.post(
  '/upload',
  uploadFile,
  async function postUpload(req: Request, res: Response) {
    const formFile = req.files

    const fieldUpload = _.get(formFile, 'fileUpload', {})

    console.log(fieldUpload)
  }
)
```

#### Using All Parameters useMulter

```javascript
import { useMulter } from 'expresso-hooks'

// multer config
const uploadFile = useMulter({
  dest: 'public/uploads',
  allowedExt: ['.pdf'],
  allowedMimetype: ['application/pdf'],
  limit: {
    fieldSize: 10 * 1024 * 1024, // 10 mb
    fileSize: 1 * 1024 * 1024, // 1 mb
  },
}).fields([
  { name: 'fileLogo', maxCount: 1 },
  { name: 'fileDocument', maxCount: 1 },
])
```
