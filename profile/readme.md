# Kitwork

> **Logic is the soul of machines.**

A Go-native bytecode runtime for ultra-fast backend logic.

```javascript id="z2r7km"
import { router, log, database } from 'kitwork';

const db = database.connect();

router.get("/").handle((req, res) => {
    go(() => db.greetings.create({
        message: "Hello from Kitwork"
    }));

    go(() => log.Print("Concurrency simplified."));

    return res.html("<h1>Hello World</h1>");
});
```

Compile once. Execute instantly.
No V8. No ORM overhead. Only execution.

> I simply want to create an environment for logic.
>         — [Huỳnh Nhân Quốc](https://github.com/huynhnhanquoc)

* [Engine](https://github.com/kitwork/engine)
* [Website](https://kitwork.io)

