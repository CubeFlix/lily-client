# lily-js

The Lily JavaScript client API, for NodeJS.

## Usage

```
import { Client, Request, UserAuth } from "lily-client";
import * as fs from 'fs';

const client = new Client("127.0.0.1", 42069, {rejectUnauthorized: false});
const resp = await client.requestNoChunks(new Request("listdir", new UserAuth("admin", "admin"), {drive: "lily", path: "."}));
console.log(resp.data.list);

resp = await client.download(new UserAuth("admin", "admin"), "lily", "1.0.0/packages/lily/source/main.go");
console.log(resp.content);

const fileContent = fs.readFileSync("myfile.txt")
resp = await client.upload(new UserAuth("admin", "admin"), "lily", "newfile.txt", fileContent);
console.log(resp);
```