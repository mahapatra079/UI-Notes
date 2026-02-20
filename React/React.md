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
Users report app freezes when typing in search input.
How do you handle API failures?
How do you deploy React app?
Difference between dev & production build?
How environment variables are managed?
What is Storybook in React?
What is CI/CD?


Final Strategy  - React internals
                - Performance optimization
                - Project architecture
                - Production debugging stories
                - One strong conflict-handling story
                - One leadership story
                - One tight deadline story
                - Error Boundaries
                - Suspense & lazychalti
                - Code splitting
                - Security (XSS, token storage)
                - Authentication flow
                - Role-based access
                - Testing (Jest / React Testing Library)
                - Git workflow (branching strategy)



1) How do you structure a large React application?

    In large React applications, I prefer a feature-based folder structure instead of grouping by component based structure. 
    Each feature contains its own components, hooks, services, and state files. This improves scalability and team collaboration.

    I separate UI components from business logic using custom hooks, and API logic is handled in service files.

    For state management, I choose tools based on complexity — local state for small components, Context for moderate sharing,
    and Redux Toolkit for enterprise-level global or server state.

    I also implement lazy loading and code splitting to improve performance and maintain a shared folder for reusable UI components.


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
                    

2) How do you manage global state in enterprise apps?

   -  I first classify state into UI state, shared client state, and server state.
   -  For UI state, I use local hooks like useState or useReducer.
   -  For shared business state, I use Redux Toolkit because it provides predictable state management, DevTools support, and better scalability.
   -  For server state, I prefer React Query or RTK Query since they handle caching, background refetching, and synchronization efficiently.
   -  I also ensure performance by normalizing data, using memoized selectors, and avoiding unnecessary global state.


3) When to use Context vs Redux?

    - I use Context for small, stable state like theme or authentication because it's lightweight and built into React.
    - For Large application I use Redux Toolkit because it provides predictable state management, DevTools support, and better scalability.

    Note: Context is suitable for simple global values, while Redux is better for complex, business-critical state.


4) How do you handle reusable components?

   - In a component-based architecture, I separate reusable components into a shared folder where they are fully props-driven and free from business logic.

   - Feature-specific logic is extracted into custom hooks within the feature module. This keeps UI components clean and maintainable.

   - For performance, I ensure components are pure and use memoization where required to prevent unnecessary re-renders.


5) What is Storybook in React? 

    StoryBook = Storybook is a tool used to build and test in React components. It helps in documenting reusable components,
                maintaining design consistency, and improving collaboration between developers and designers.

                - An open-source development environment and tool that runs alongside your React.

             Analysis : 

                         -  Developers build reusable components (Button, Modal, Input, Card)

                         -  Designers want to review UI

                         -  QA wants to test component states

                         -  Teams need documentation

                         -  Instead of running the entire app, Storybook lets you see components individually.

             Example : 
                        
                            Suppose you have a Button component.

                            With Storybook, you can show:

                            Primary button

                            Secondary button

                            Disabled button

                            Loading button

                            All in one place.

                            You don’t need backend or routing to test it.

             
             Benifits : 

                        -   Component documentation

                        -   Visual testing

                        -   Design system consistency

                        -   Team collaboration

                        -  Easy UI review

                        -  Faster development
                            
    
        Note: Storybook runs on a separate local server

              extension file name :  Task.stories.tsx    

              ES6 - Recommended is Component Story Format (CSF) ; an open standard based on ES6 modules that is portable beyond Storybook.
             
              ES Modules. Every component story file consists of a required default export and one or more named exports.
        