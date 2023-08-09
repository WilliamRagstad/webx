
<br>
<img src="assets/logo.png" height="80px" />

This is the official repository for the WebX web server project.
A framework for building minimal but powerful backends for web applications.\
▸ [Get started](#getting-started) or [read more](#why-webx) about the project below.

> **⚠️ WebX is still in early development and is not ready for use in production.**

<br>

## Features & Roadmap
Below is a high-level overview of the existing (implemented) and planned features of the WebX technology (in no particular order).
- [X] Blazingly fast 🔥
- [X] Lightweight 🪶
- [X] Simple and intuitive 🧠
- [X] Command line interface (CLI)
- [ ] WebX DSL (Domain Specific Language)
  - [X] Project structure
  - [ ] Parser module
  - [ ] Engine module
  - [ ] Comments
  - [ ] Routing
  - [ ] SSR JSX support
  - [ ] TypeScript integration
    - [ ] WebAssembly support
    - [ ] Unified type definitions
  - [ ] Built-in ORM (Prism like)
    - [ ] Model definitions
    - [ ] Queries
    - [ ] Migrations
  - [ ] Validation
  - [ ] Handlers
  - [ ] Middleware
  - [ ] Error handling
  - [ ] Templating
  - [ ] Authentication
  - [ ] Authorization
  - [ ] Built-in services
    - [ ] Sessions
    - [ ] Caching
    - [ ] Static file serving
    - [ ] WebSockets
- [ ] Package management (NPM like)
- [ ] Integrated testing framework/suite
- [ ] Batteries included 🔋 (large stdlib)
- [ ] Language server protocol
- [ ] VSC extension (syntax highlighting, snippets, etc.)
- [ ] Hot reloading
- [ ] Production mode
- [ ] TLS/SSL/HTTPS support
- [ ] Database drivers (PostgreSQL, MySQL, SQLite)
- [ ] DDOS protection 🛡️
- [ ] Input sanitization (safe defaults)
- [ ] Output sanitization (safe defaults)

Do you have any suggestions for additional features?
Create an issue or a pull request!
[Read more](#contributing) about contributing below.

<br>

## Getting started
### Installation
Download the latest prebuilt binaries from the [releases page](https://github.com/WilliamRagstad/WebX/releases) and extract it to a folder of your choice.

### Usage
To start the web server for a project, use:
```sh
webx run
```

To run the project in production mode, use:
```sh
webx run --prod
```

<br>

## Examples
The following is an example of a simple WebX todo list application.
```typescript
model User {
  id: number @primary @autoincrement;
  name: string[maxLength(50))]
  email: string?; // optional
  isAdmin: boolean;
}

model Todo {
  id: number @primary @autoincrement;
  task: string;
  userId: number @foreign(User.id);
}

handler initServices() { 
  userService: new UserService(),
  todoService: new TodoService()
}

handler auth(userService: UserService, id: number) {
  user: userService.getCurrentUser(id)
}

handler isAdmin(user: User) {
  if (!user.isAdmin()) {
    return error("User is not an admin.");
  }
}

handler renderTodos(todos: Todo[], user: User): HTML {
  return (<div>
      <h1>Welcome, {user.name}!</h1>
      <ul>
        {todos.map(todo => <li>{todo.task}</li>)}
      </ul>
    </div>);
}

// Endpoint: GET /todos/<user id>
get /todos/(id: number) -> initServices(), auth($.userService, id), isAdmin($.user) {
    const todos = $.todoService.getAllTodosForUser($.user.id);
    return { todos };
} -> renderTodos($.todos, $.user)
```

<br>

## Why Web<font color="#3d72d7">X</font>?
**Our vision** is to reduce the boilerplate and complexity of building backends and APIs.\
▸ WebX is designed to be **simple**, **minimal**, **easy to learn**, and **intuitive** while still being **versatile** and **flexible**.
It is capable of building complex applications **quickly** while still being **lightweight🪶** and **blazingly fast🔥**.

> **Backends shouldn't be bloated and complex**, but focus on what's most important.
> Don't reinvent the wheel for every new project,\
> ▸ Jump straight to ***the goodi-goodi parts*** and get [started using](#getting-started) **WebX** today!

### ❤️ Perfect match for <b><<font color="#3d72d7">/</font>> htm<font color="#3d72d7">x</font></b>
WebX is designed to be a minimalistic web framework that is easy to learn and use.
It is ***intended*** to be used with **HTMX**, which is a great alternative to frameworks like React, Vue, and Angular (or other stacks).
HTMX allows you to build dynamic web applications without having to learn a new language or framework for the frontend.
WebX is designed to be versatile and flexible, and it is easy to build backends for complex applications quickly.

<br>

## Contributing
Contributions are welcome!
If you have any suggestions or find any bugs, please create an issue or a pull request.