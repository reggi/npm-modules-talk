npm modules

---

https://github.com/reggi/npm-modules-talk

---
<center>
Thomas Reggi
</center>

* `@reggi` on github
* `@thomasreggi` on twitter

---

![work](./gifs/work.png)

---

<br><br>
why bother creating node modules?
<br><br>

---

1. reusable 
  * `npm i my-mod`
2. versioned (semver)
  * `1.0.0` -> `1.0.1`

---

my dream:

* everything I write to be reusable
* "complete library of every piece of code I write"

---

reuse as much as possibe

* un-exported functions
* functions wrapped in closures
* functions depending on globals
* functions depending on this context

---

un-exported functions 😩

![minimist example](./gifs/minimist-example.png)

---

this everywhere 🚀

![git this](./gifs/git-this.png)

---

<br><br>
how do we create a node module?
<br><br>

---

__Files!__

1. `package.json`
2. `index.js`

---

__`package.json`__

```json
{
  "name": "node-modules-talk",
  "version": "1.0.0",
  "main": "index.js"
}
```

---

__`package.json` with scope__

```json
{
  "name": "@reggi/node-modules-talk",
  "version": "1.0.0",
  "main": "index.js",
  "publishConfig": {
    "access": "public"
  }
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

now that it's publshed what...

1. Check it's available `npm view`
2. Check if it's `requireable`

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

nope

![kanye](./gifs/kanye-no.gif)

---

__check our work__


```bash
mkdir check-our-work
```

<hr>

```bash
cd check-our-work
touch index.js
```

<hr>

```bash
npm init -y
```

<hr>

```bash
npm install npm-modules-talk --registry http://localhost:4873/
```

<hr>

```js
const winning = require('npm-modules-talk')
console.log(winning) // should log "Hello world"
```

<hr>

```js
node index.js
```

---

running the node file that uses the node module

```bash
node ./index.js
```

![results](./gifs/results.gif)

---

<br><br>
pro tips 💅
<br><br>

---

1. `.npmignore`
2. `monorepo`
3. jenkins
4. private registries

---

What is `.npmignore`?

---

Just like `.gitignore` but for `npm`.

```
__snapshots__
coverage
screenshots
examples
index.js
index.test.js
test.js
.pkgrc
.gitignore
example
package-local.json
node_modules
```

---

Tar without ignore:

![module-without-ignore.png](./gifs/module-without-ignore.png)

---

Tar with ignore:

![module-with-ignore.png](./gifs/module-with-ignore.png)

---

What is a monorepo?

---

Everybody loves dragons.

![lerna](./gifs/lerna-home.png)

---

single repo many packages

![monorepo-packages](./gifs/monorepo-packages.png)

---

each module is small

![monorepo-example](./gifs/monorepo-example.png)

---

consume your own modules

![lerna-example](./gifs/lerna-example.png)

---

jenkins is your friend

![jenkins](./gifs/jenkins.png)

---

run on jenkins

* `depcheck`
* `standard`
* `tests` (with 100% coverage)
* `publish`

---

What is a private registry?

---

issues happen, centralization 🌋🔒😿

![npm-issue](./gifs/npm-issue.png)

---

have a backup.

![reggi-registry](./gifs/reggi-registry.png)

---

have no fear

---

story time

---

my first node module

![npm-scheme](./gifs/npm-scheme.png)

---

what it did, was dumb

![node-url](./gifs/node-url.png)

---

how it did it, was even dumber

![npm-scheme-deps](./gifs/npm-scheme-deps.png)

---

php?

![github-scheme](./gifs/github-scheme.png)

---

so don't worry! don't fear the `npm publish` command

---

the end

---

https://github.com/reggi/npm-modules-talk
<br>
Thomas Reggi
