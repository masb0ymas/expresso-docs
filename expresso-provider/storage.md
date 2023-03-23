# storage

{% hint style="info" %}
Storage Provider for expressjs
{% endhint %}

Using commonjs

```javascript
const { Storage } = require('expresso-provider')
```

Using ES6

```javascript
import { Storage } from 'expresso-provider'
```

### Initialize Storage

```javascript
import { Storage } from 'expresso-provider'
import path from 'path'

const serviceAccountPath = path.resolve(
  `${process.cwd()}/public/gcp/gcp_serviceAccount.json`
)

export const storageService = new Storage({
  provider: 'gcp',
  accessKey: 'your_app_gcp',
  bucket: 'your_bucket_name',
  region: 'asia-southeast2',
  expires: '5d',
  options: {
    filePath: serviceAccountPath,
  },
})

storageService.initialize()
```

### Upload File for JavaScript

```javascript
import { storageService } from 'config/storage'

async function uploadFile({ fieldUpload, directory, UploadId }) {
  const { expiryDate } = storageService.expiresObject()
  const keyFile = `${directory}/${fieldUpload.filename}`

  const { signedURL } = await storageService.uploadFile(fieldUpload, directory)

  const formUpload = {
    ...fieldUpload,
    keyFile,
    signedURL,
    expiryDateURL: expiryDate,
  }

  return formUpload
}
```

### Upload File for TypeScript

```typescript
import { storageService } from 'config/storage'
import { type Storage } from '@google-cloud/storage'

interface FileAttributes {
  fieldname: string
  originalname: string
  encoding: string
  mimetype: string
  destination: string
  filename: string
  path: string
  size: number
}

interface UploadFileEntity {
  fieldUpload: FileAttributes
  directory: string
  UploadId?: string | null
}

async function uploadFile({ fieldUpload, directory, UploadId }: UploadFileEntity): Promise<{
  storageResponse: any
  uploadResponse: Upload
}> {
  const { expiryDate } = storageService.expiresObject()
  const keyFile = `${directory}/${fieldUpload.filename}`

  const { signedURL } = await storageService.uploadFile<Storage>(fieldUpload, directory)

  const formUpload = {
    ...fieldUpload,
    keyFile,
    signedURL,
    expiryDateURL: expiryDate,
  }

  return formUpload
}
```

### Get Presigned URL

```javascript
import { storageService } from 'config/storage'

const keyFile = 'uploads/any_image.png'

const signedURL = await storageService.getPresignedURL(keyFile)
```
