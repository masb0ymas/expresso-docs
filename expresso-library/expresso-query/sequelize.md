# Sequelize

{% hint style="info" %}
useQuery Sequelize to Simplify Query Management data
{% endhint %}

{% embed url="https://www.npmjs.com/package/sequelize" %}
sequelize query
{% endembed %}

Using commonjs

```javascript
const { useSequelize } = require('expresso-query')
```

Using ES6

```javascript
import { useSequelize } from 'expresso-query'
```

#### Using All Parameter useSequelize

<pre class="language-javascript"><code class="lang-javascript">import { useSequelize } from 'expresso-query'
import { User } from 'database/entities/User'
import { Role } from 'database/entities/Role'
import route from 'routes/v1'

route.get(
  '/user',
  async function findAll(req: Request, res: Response) {
  const reqQuery = req.query
  
  const relations = [{ model: Role }]
  
  const query = useSequelize.queryBuilder({ 
    entity: User, 
    reqQuery, 
    includeRule: useSequelize.makeIncludeQueryable(reqQuery.filtered, relations),
  }, { type: 'postgres' })
  
<strong>  const data = await User.findAll({
</strong>      ...query,
      order: query.order ? query.order : [['createdAt', 'desc']],
  })

  const total = await User.count({
      include: query.includeCount,
      where: query.where,
  })

  return res.status(200).json({ data, total })
})

</code></pre>
