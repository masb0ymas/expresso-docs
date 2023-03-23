# typeorm

{% hint style="info" %}
useQuery TypeORM to Simplify Query Management data
{% endhint %}

Using commonjs

```javascript
const { useQueryTypeORM } = require('expresso-query')
```

Using ES6

```javascript
import { useQueryTypeORM } from 'expresso-query'
```

#### Using All Parameter useQueryTypeORM

```javascript
import { useQueryTypeORM } from 'expresso-query'
import AppDataSource from 'database/data-source'
import { Role } from 'database/entities/Role'
import route from 'routes/v1'

route.get(
  '/role',
  async function findAll(req: Request, res: Response) {
  const reqQuery = req.query

  const roleRepository = AppDataSource.getRepository(Role)
  
  const query = roleRepository.createQueryBuilder()
  const newQuery = useQueryTypeORM({ entity: 'Role', query, reqQuery }, { type: 'postgres' })
  
  const data = await newQuery.getMany()
  const total = await newQuery.getCount()

  return res.status(200).json({ data, total })
})

```
