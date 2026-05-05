# TodoList

A React to-do list app that seeds tasks from a live REST API and supports adding, completing, and deleting items. Built as an introduction to React class components, client-side routing, prop drilling, PropTypes validation, and Axios-based API integration.

---

## ✅ Features

- **Seeded from API** — on mount, fetches 10 todos from the [JSONPlaceholder](https://jsonplaceholder.typicode.com) REST API as initial state
- **Add todo** — controlled input form posts a new item to the API and appends the response to the list
- **Mark complete** — checkbox toggles a strikethrough style on the todo title
- **Delete todo** — sends a DELETE request to the API and removes the item from local state
- **Client-side routing** — `react-router-dom` handles `/` (todo list) and `/about` routes without a page reload
- **PropTypes validation** — all components declare required props with `PropTypes` for runtime type checking

---

## 🗂️ Project Structure

```
src/
├── App.js                      # Root class component — state, API calls, route definitions
├── components/
│   ├── AddTodo.js              # Controlled form component for new todo input
│   ├── TodoItem.js             # Individual todo row — checkbox, title, delete button
│   ├── Todos.js                # List renderer — maps todos to TodoItem components
│   ├── layout/
│   │   └── Header.js           # Navigation header with Home / About links
│   └── pages/
│       └── About.js            # Static about page
└── App.css                     # Global styles
```

---

## 🔌 API Integration

All HTTP calls use `axios` against the [JSONPlaceholder](https://jsonplaceholder.typicode.com) mock API:

| Action | Method | Endpoint |
|---|---|---|
| Load initial todos | `GET` | `/todos?_limit=10` |
| Add a todo | `POST` | `/todos` |
| Delete a todo | `DELETE` | `/todos/:id` |

> JSONPlaceholder is a read-only mock API — changes do not persist server-side, but the responses mirror real REST behaviour for development purposes.

---

## 🧩 Component Overview

**`App`** — Class component holding `todos` state. Fetches seed data in `componentDidMount`. Passes `markComplete`, `delTodo`, and `addTodo` handlers down as props. Wraps everything in `BrowserRouter` and defines routes.

**`AddTodo`** — Class component with controlled `title` state. Clears the input on submit and calls the `addTodo` prop with the entered title.

**`Todos`** — Stateless class component that maps the `todos` array to individual `TodoItem` components, forwarding `markComplete` and `delTodo` props.

**`TodoItem`** — Renders a single row with a checkbox, title, and delete button. Applies `text-decoration: line-through` via `getStyle()` when `todo.completed` is true.

**`Header`** — Functional component rendering a styled nav bar with `react-router-dom` `<Link>` elements.

---

## 🚀 Getting Started

```bash
git clone https://github.com/Andytule/to-do-list.git
cd to-do-list
npm install
npm start
```

Open [http://localhost:3000](http://localhost:3000) in your browser.

---

## 🛠️ Tech Stack

| Technology | Usage |
|---|---|
| React 16 | Class and functional components |
| Axios | REST API requests |
| react-router-dom v5 | Client-side routing (`BrowserRouter`, `Route`, `Link`) |
| PropTypes | Runtime prop type validation |
| JSONPlaceholder | Mock REST API for todos |

---

## 📄 License

See [LICENSE](LICENSE) for details.
