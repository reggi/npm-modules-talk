npm modules

---

__me__

* Thomas Reggi
* amex developer for ~1 year
* thomas@reggi.com
* `@reggi` on github
* `@thomasreggi` on twitter

---

why?

---

1. reusable 
  * `npm i my-mod`
2. versioned (semver)
  * `1.0.0` -> `1.0.1`

---

reuse as much as possibe

* un-exported functions
* functions wrapped in closures
* functions depending on globals
* functions depending on this context

---

![minimist example](./gifs/minimist-example.png)

---

how?

---

__Files!__

1. `package.json`
2. `index.js`

---

__`package.json`__

```json
{
  "name": "thomas-reggi-npm-talk",
  "version": "1.0.0",
  "main": "index.js"
}
```

---

__`main.js`__

```js
module.exports = "Hello world"
```

---

now what?

---

publishing!

---

0. About registries
1. `npm login`
2. `npm publish`

---

![verdaccio](./gifs/verdaccio-home.png)

--- 

__registry flag__

flag:

* `npm login --registry (registry-url)`
* `npm publish --registry (registry-url)`
* `npm set registry http://localhost:4873`

examples:

* https://registry.npmjs.org/
* https://registry.reggi.com/ (proxy)
* http://localhost:4873/ (proxy)

---

__npm login__

```
npm login --registry http://localhost:4873
```

---

__npm publish__

```bash
npm publish --registry http://localhost:4873/
```

![npm publish](./gifs/npm-publish.gif)

---

using the `npm view` command

---

__npm view__

```bash
npm view npm-modules-talk --registry http://localhost:4873/
```

![npm view](./gifs/npm-view.gif)

---

__npm view version__

```bash
npm view npm-modules-talk version --registry http://localhost:4873/
```

![npm view](./gifs/npm-view-version.gif)

---

![party](./gifs/party.png)

---

```bash
npm install npm-modules-talk --registry http://localhost:4873/
```

<hr>

```js
const winning = require('npm-modules-talk')
console.log(winning)
```

<hr>

```js
node index.js
```

---

![results](./gifs/results.gif)

---

my dream:

* everything I write to be reusable
* "complete library of every piece of code I write"

---

`monorepo`

---

Lerna

![lerna](./gifs/lerna-home.png)

---

![monorepo-packages](./gifs/monorepo-packages.png)

---

![monorepo-example](./gifs/monorepo-example.png)

---

the end

