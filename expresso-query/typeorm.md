# TypeORM

{% hint style="info" %}
useQuery TypeORM to Simplify Query Management data
{% endhint %}

{% embed url="https://www.npmjs.com/package/typeorm" %}
query typeorm
{% endembed %}

Using commonjs

```javascript
const { useTypeOrm } = require('expresso-query')
```

Using ES6

```javascript
import { useTypeOrm } from 'expresso-query'
```

#### Using All Parameter useTypeOrm

```javascript
import { useTypeOrm } from 'expresso-query'
import AppDataSource from 'database/data-source'
import { Role } from 'database/entities/Role'
import route from 'routes/v1'

route.get(
  '/role',
  async function findAll(req: Request, res: Response) {
  const reqQuery = req.query

  const roleRepository = AppDataSource.getRepository(Role)
  
  const query = roleRepository.createQueryBuilder()
  const newQuery = useTypeOrm.queryBuilder({ entity: 'Role', query, reqQuery }, { type: 'postgres' })
  
  const data = await newQuery.getMany()
  const total = await newQuery.getCount()

  return res.status(200).json({ data, total })
})

```
