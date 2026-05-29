## Node.js
Node.js is an **open-source**, **cross-platform**, **back-end**, JavaScript **runtime environment** that executes JavaScript code outside a web browser

- Open source - because it’s source code is available for use and modification legally
- Cross platform - works across different platforms like Linux, OSX and Windows
- Backend - receives requests from clients and contains the logic to respond to it
- JS runtime environment - where JavaScript code gets parsed and executed

Normally, JavaScript runs in a browser to make websites interactive. For example, clicking buttons, showing popups, validating forms, etc.

Node.js lets you use JavaScript to build things like:
- backend servers
- APIs
- command-line tools
- chat apps
- file-processing scripts
- real-time apps
- automation tools

```jsx
**JavaScript in browser** = controls the webpage

**JavaScript in Node.js** = controls the server, files, databases, and backend logic
```

To Use Node.js, we need to install Node.js to the system.

---
## NPM — Node Package Manager

### What is NPM?
**NPM** is the default package manager for **Node.js**. It is a tool that lets you:

- **Install** third-party libraries (called _packages_ or _dependencies_) into your project
- **Manage** those dependencies (update, remove, version-control them)
- **Run scripts** like starting a server, running tests, or building your app
- **Publish** your own packages to the npm registry for others to use

Think of npm like an **app store for JavaScript code** — instead of writing everything from scratch, you pull in pre-built, tested libraries.

### Why Do We Need NPM?
Without NPM, you'd have to:
- Manually download every library
- Track versions yourself
- Share code by sending zip files

With NPM, you just run one command and everything installs automatically. It also ensures your whole team uses the **exact same versions** of every library.

---
### Key Files
`package.json` - This is the **heart of your project**. It's a JSON file that stores:

```json
{
  "name": "my-app",
  "version": "1.0.0",
  "scripts": {
    "start": "node index.js",
    "test": "jest"
  },
  "dependencies": {
    "express": "^4.18.2"
  },
  "devDependencies": {
    "jest": "^29.0.0"
  }
}
```

|Section|Purpose|
|---|---|
|`name` / `version`|Identifies your project|
|`scripts`|Shortcuts for commands you run often|
|`dependencies`|Packages needed in **production**|
|`devDependencies`|Packages only needed during **development** (testing, building)|

`package-lock.json`
This file is **auto-generated** by npm. It locks the **exact version** of every installed package (including sub-dependencies). This guarantees that if someone else clones your project, they get the **identical** package tree — no surprises.

> Always commit `package-lock.json` to version control. Never edit it manually.

---
### Essential NPM Commands

Setup & Install

```bash
npm init          # Create a new package.json (interactive)
npm init -y       # Create package.json with all defaults

npm install       # Install all dependencies from package.json
npm install express          # Install a specific package
npm install jest --save-dev  # Install as a dev dependency
```

Running / Starting

```bash
npm start         # Runs the "start" script in package.json
npm run dev       # Runs the "dev" script
npm test          # Runs the "test" script
npm run build     # Runs the "build" script
```

Update & Remove

```bash
npm update              # Update all packages
npm uninstall express   # Remove a package
```

Info

```bash
npm list          # List installed packages
npm outdated      # See which packages have newer versions
```

---