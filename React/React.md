# Strategy 

How do you structure a large React application? - component based  + feature based 
How do you manage global state in enterprise apps?
When to use Context vs Redux?
How do you handle reusable components?
How do you prevent re-renders?
What is reconciliation?
How to improve large table performance?
Why Virtual DOM is faster?
When to use useMemo?
Production build is slow. What will you check?
Production bug is reported. What steps will you follow?
How do you debug production bugs?
Users report app freezes when typing in search input.
How do you handle API failures?
How do you deploy React app?
Difference between dev & production build?
How environment variables are managed?
What is Storybook in React?
What is CI/CD?
How do you secure API calls?
What happens when API is slow?
How do you optimize large tables?
Middleware
HOC

If you have a dynamic array of objects and the user wants to access only the name field, you simply extract that property.

You are given an array of objects containing user information (for example, each object has a name property).
There is a search input field in the UI.
How would you implement a dynamic search functionality that filters and displays only the users whose names match the entered search text

Final Strategy  - React internals
                - Performance optimization
                - Project architecture
                - Production debugging stories
                - One strong conflict-handling story
                - One leadership story
                - One tight deadline story
                - Error Boundaries
                - Suspense & lazy
                - Code splitting
                - Security (XSS, token storage)
                - Authentication flow
                - Role-based access
                - Testing (Jest / React Testing Library)
                - Git workflow (branching strategy)



## 1) How do you structure a large React application?

In large React applications, I prefer a feature-based folder structure instead of grouping by component type. Each feature contains its own components, hooks, services, and state files. This improves scalability and team collaboration.

I separate UI components from business logic using custom hooks, and API logic is handled in service files.

For state management, I choose tools based on complexity — local state for small components, Context for moderate sharing, and Redux Toolkit for enterprise-level global or server state.

I also implement lazy loading and code splitting to improve performance and maintain a shared folder for reusable UI components.

```
src/
    ├── app/                # App setup (routing, store)
    ├── features/
    │    ├── auth/
    │    │    ├── components/
    │    │    ├── hooks/
    │    │    ├── services/
    │    │    ├── authSlice.js
    │    │    └── index.js
    │    ├── dashboard/
    │    └── users/
    ├── shared/             # Reusable components
    ├── hooks/              # Global custom hooks
    ├── utils/
    └── routes/
```


## 2) How do you manage global state in enterprise apps?

- I first classify state into UI state, shared client state, and server state.
- For UI state, I use local hooks like useState or useReducer.
- For shared business state, I use Redux Toolkit because it provides predictable state management, DevTools support, and better scalability.
- For server state, I prefer React Query or RTK Query since they handle caching, background refetching, and synchronization efficiently.
- I also ensure performance by normalizing data, using memoized selectors, and avoiding unnecessary global state.


## 3) When to use Context vs Redux?

- I use Context for small, stable state like theme or authentication because it's lightweight and built into React.
- For Large application I use Redux Toolkit because it provides predictable state management, DevTools support, and better scalability.

**Note:** Context is suitable for simple global values, while Redux is better for complex, business-critical state.


## 4) How do you handle reusable components?

- In a component-based architecture, I separate reusable components into a shared folder where they are fully props-driven and free from business logic.
- Feature-specific logic is extracted into custom hooks within the feature module. This keeps UI components clean and maintainable.
- For performance, I ensure components are pure and use memoization where required to prevent unnecessary re-renders.


## 5) What is Storybook in React?

Storybook is a tool used to build and test React components in isolation. It helps in documenting reusable components, maintaining design consistency, and improving collaboration between developers and designers.

- An open-source development environment and tool that runs alongside your React app.

**Analysis:**
- Developers build reusable components (Button, Modal, Input, Card)
- Designers want to review UI
- QA wants to test component states
- Teams need documentation
- Instead of running the entire app, Storybook lets you see components individually.

**Example:**

Suppose you have a Button component. With Storybook, you can show:
- Primary button
- Secondary button
- Disabled button
- Loading button

All in one place. You don't need backend or routing to test it.

**Benefits:**
- Component documentation
- Visual testing
- Design system consistency
- Team collaboration
- Easy UI review
- Faster development

**Note:** Storybook runs on a separate local server. Extension file name: `Task.stories.tsx`. ES6 - Recommended is Component Story Format (CSF); an open standard based on ES6 modules that is portable beyond Storybook.


## 6) Reconciliation

Reconciliation is React's process of comparing the previous and new Virtual DOM using its diffing algorithm and updating only the necessary parts of the real DOM to optimize performance.

**Why It's Needed?**
- Updating the real DOM directly is slow.

So React:
- Creates a Virtual DOM
- Compares old vs new version (Diffing)
- Applies minimal updates
- This makes UI updates efficient.

**Diffing Algorithm:**

The Diffing Algorithm in React is the process of comparing the old and new Virtual DOM to identify changes and update only the necessary parts of the real DOM efficiently.

**Examples:**

If a list of items changes, React identifies which items were added, removed, or updated and only modifies those specific DOM nodes.

```
Before: [A, B, C]
After:  [A, D, C]
React updates only B to D instead of re-rendering the entire list.
```

```html
<div> Hello </div>  <!-- Old Node -->
<span> Hello </span> <!-- New Node -->
```
Since div ≠ span, React removes the old node and creates a new one.

**Special Case: Lists & Keys**

When rendering lists, React uses keys to track items.

```jsx
{items.map(item => (
    <li key={item.id}>{item.name}</li>
))}
```

Keys help React:
- Identify which item changed
- Detect moved elements
- Avoid unnecessary re-renders
- Without keys → React compares by position → less efficient.


## 7) Why Virtual DOM is Faster?

Virtual DOM makes updates faster because it reduces expensive operations on the real DOM.

Virtual DOM is faster because React updates changes in memory first, uses a diffing algorithm to detect minimal changes, and updates only the necessary parts of the real DOM, reducing expensive DOM operations.

## 8) Is Virtual DOM Always Faster?

No, Virtual DOM is not always faster. It improves performance by minimizing real DOM updates in complex applications, but for small or simple updates, direct DOM manipulation can be faster because Virtual DOM adds comparison overhead.

**Note:** Virtual DOM is an optimization strategy to reduce DOM manipulation — not a guarantee of speed. The real DOM is slow. Virtual DOM minimizes touching it.


## 9) Extracting Specific Fields from Dynamic Array

If you have a dynamic array of objects and the user wants to access only the name field, you simply extract that property.

**1) Get Only Names Using Map:**

```javascript
const users = [
    { id: 1, name: "Amit", age: 25 },
    { id: 2, name: "Rahul", age: 30 },
    { id: 3, name: "Priya", age: 28 }
];

const names = users.map(user => user.name);
console.log(names);
```

**2) Rendering On Browser:**

```jsx
{users.map(user => (
    <p key={user.id}>{user.name}</p>
))}
```

**3) If Array is Dynamic (API Response):**

```javascript
const response = {
    data: [
        { id: 1, name: "Amit", age: 25 },
        { id: 2, name: "Rahul", age: 30 },
        { id: 3, name: "Priya", age: 28 }
    ]
};

const names = response.data.map(item => item.name);
console.log(names);
```

**Note:** If I need only the name from a dynamic array of objects, I use `map()` to extract the name property and create a new array.


## 10) Dynamic Search Functionality

You are given an array of objects containing user information (for example, each object has a name property). There is a search input field in the UI. How would you implement a dynamic search functionality that filters and displays only the users whose names match the entered search text?

```jsx
import React, { useState } from "react";

function App() {
    const [search, setSearch] = useState("");

    const users = [
        { id: 1, name: "Amit" },
        { id: 2, name: "Rahul" },
        { id: 3, name: "Priya" },
        { id: 4, name: "Anita" }
    ];

    const filteredUsers = users.filter(user =>
        user.name.toLowerCase().includes(search.toLowerCase())
    );

    return (
        <div>
            <input
                type="text"
                placeholder="Search name..."
                value={search}
                onChange={(e) => setSearch(e.target.value)}
            />

            {filteredUsers.map(user => (
                <p key={user.id}>{user.name}</p>
            ))}
        </div>
    );
}

export default App;
```

**Notes:**
- I use the `filter()` method to compare the search input with the name property using `includes()` and return matching results.
- I convert both name and search text to lowercase and use `includes()` to perform case-insensitive filtering.
- `(user.name || "").toLowerCase().includes(search.toLowerCase())` prevents errors if name is undefined.
- `toLowerCase()` is not mandatory, but it is used to make search case-insensitive and improve user experience.
- `user.name.includes(search);` - Without toLowerCase (Case-Sensitive). User must match exact casing.


## 11) How Environment Variables Are Managed?

Environment variables are managed using `.env` files and accessed through `process.env` or `import.meta.env` depending on the build tool.

Separate environment files are used for development and production, and sensitive secrets are stored only in the backend or injected through CI/CD pipelines.

**Note:** Environment variables are configuration values stored outside the code.

**Create a file:**

```
.env
```

**Example:**

```
VITE_API_URL=https://api.example.com
VITE_APP_NAME=MyApp
```

**Environment-Based Files:**

You can create multiple files:
- `.env.development`
- `.env.production`
- `.env.test`

**Examples:**
- API URLs
- Secret keys
- Database URLs
- Feature flags
- App mode (development / production)

**They help us:** Change configuration without changing source code.


## 12) HOC (Higher-Order Components)

HOC are functions that take a component and return a new component with enhanced functionality. They are used to reuse component logic across multiple components.

**Why Use HOC?**
- Reuse logic across multiple components
- Add extra functionality (auth, logging, loading, permissions)
- Avoid code duplication

**HOC vs Hooks:**

| HOC             | Hooks                       |
| --------------- | --------------------------- |
| Wraps component | Used inside component       |
| Reusable logic  | Reusable logic              |
| Older pattern   | Modern recommended approach |


**Syntax**
```jsx
const EnhancedComponent = withEnhancement(OriginalComponent);
```

- higherOrderComponent → a function
- WrappedComponent → the original component
- EnhancedComponent → the new component returned by the HOC

**Example:**

```jsx
function withAuth(Component) {
    return function AuthenticatedComponent(props) {
        const isAuthenticated = // logic to check auth
        if (!isAuthenticated) {
            return <Redirect to="/login" />;
        }
        return <Component {...props} />;
    };
}
```

In this example, `withAuth` is a HOC that wraps a component and checks if the user is authenticated. If not, it redirects to the login page. Otherwise, it renders the original component with its props.