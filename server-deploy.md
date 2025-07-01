## Server Deployment steps

1. comment await commands outside api methods for solving gateway timeout error

```js
//comment following commands
await client.connect();
await client.db("admin").command({ ping: 1 });
```

2. create vercel.json file for configuring server

```json
{
  "version": 2,
  "builds": [
    {
      "src": "index.js",
      "use": "@vercel/node"
    }
  ],
  "routes": [
    {
      "src": "/(.*)",
      "dest": "index.js",
      "methods": ["GET", "POST", "PUT", "PATCH", "DELETE", "OPTIONS"]
    }
  ]
}
```

3. convert firbase service key to base64 string

```js
const fs = require('fs');
const key = fs.readFileSync('./firebase-admin-service-key.json', 'utf8')
const base64 = Buffer.from(key).toString('base64')
console.log(base64)
```

4. use the service account from env variable

```js
// const serviceAccount = require("./firebase-admin-key.json");

const decoded = Buffer.from(process.env.FB_SERVICE_KEY, 'base64').toString('utf8')
const serviceAccount = JSON.parse(decoded);
```


5. Deploy to Vercel

```bash

vercel
vercel --prod
- After completed the deployment . click on inspect link and copy the production domain
```

5. Setup your environment variables in vercel
- check your public API


<img src="https://i.ibb.co.com/dgH40d3/Screenshot-3.jpg"/>

# Server Deployment on Vercel  Done
