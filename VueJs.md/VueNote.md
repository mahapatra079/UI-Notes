# Vue  - Vue is an open source JS framework used to build SPA.

1) SPA(Sinngle Page Applications) : - A Single Page Applications is a Web Application that loads a single HTML Page
                                      and dynamically updated the page as the user interacts with the app.

2) Featrues Of Vue :- 
            **Component Based Approach**
            **Template**
            **Virtual Dom**
            **Reactivity System**
            **Directives**
            **Single File Component (SFC)**
            **Progressive Framework**
            **Lightweight & Fast**
            **Vue Router & Vuex / Pinia**
            **API - Options API / Composition API**

3) Component Based Approach = A component is a reusable piece of the UI that controlls how a part of the screens looks and behaves.

                                ┌──────────────────────────────────────────┐
                                │                 App                      │
                                │  ┌─────────────────────────────────────┐ │
                                │  │             Header                  │ │
                                │  ├──────────┬──────────────────────────┤ │
                                │  │          │                          │ │
                                │  │          │                          │ │
                                │  │  Aside   │         Main             │ │
                                │  │          │                          │ │
                                │  │          │                          │ │
                                │  ├──────────┴──────────────────────────┤ │
                                │  │             Footer                  │ │
                                │  └─────────────────────────────────────┘ │
                                └──────────────────────────────────────────┘

                                                App
                                                ├── Header
                                                ├── Layout
                                                │    ├── Aside (Sidebar)
                                                │    └── Main (Content)
                                                └── Footer


4) Template = A Template deinfes the UI Structure using the HTML with declarative data binding & event handling.

             Ex:
                <template>
                  <div>
                    <h1>{{ message }}</h1>
                    <button @click="count++">Clicked {{ count }} times</button>
                  </div>
                </template>

                <script>
                export default {
                  data() {
                    return {
                      message: 'Hello Vue',
                      count: 0
                    }
                  }
                }
                </script>

5) Virtual Dom  = It is the replica of Actual DOM. When there is a change in app, changes first occurs in Virtual DOM.
                  
                  Then it compares with the Actual DOM using the internal id, to identify the difference b/w Virtual DOM.
                  & Actual DOM.

                  Then only the changed component gets re-rendered in the UI.

                  Flow:

                        ┌─────────────────────┐
                        │    Data Change      │
                        └──────────┬──────────┘
                                   ↓
                        ┌─────────────────────┐
                        │ New Virtual DOM     │
                        │     Created         │
                        └──────────┬──────────┘
                                   ↓
                        ┌─────────────────────┐
                        │ Diffing Algorithm   │
                        │ (Compare Old vs New)│
                        └──────────┬──────────┘
                                   ↓
                        ┌─────────────────────┐
                        │  Identify Changes   │
                        └──────────┬──────────┘
                                   ↓
                        ┌─────────────────────┐
                        │ Update Only Changed │
                        │  Parts in Real DOM  │
                        └──────────┬──────────┘
                                   ↓
                        ┌─────────────────────┐
                        │   UI Re-rendered    │
                        └─────────────────────┘

6) Reactivity System  = It automatically track the data changes and updates the UI; when State changes;
                        without manually manipulating DOm.

                Note: Because It removes manual manipulation DOM & Imporves Performance & Developer Productivity.

                Ex:
                    <template>
                      <div>
                        <p>{{ count }}</p>
                        <button @click="count++">Increment</button>
                      </div>
                    </template>

                    <script>
                    export default {
                      data() {
                        return {
                          count: 0  // Vue tracks this
                        }
                      }
                    }
                    </script>

                    // When count changes → UI updates automatically ✅
                    // No need: document.getElementById().innerHTML = count ❌


7) Directive = Directives are special attributes that add reactive behaviour to DOM elements.

                Types:

                    v-bind (:)  - Bind attributes
                                  Ex: <img :src="imageUrl" :alt="title" />

                    v-on (@)    - Event handling
                                  Ex: <button @click="handleClick">Click</button>

                    v-if        - Adds or Removes the element from DOM based on boolean Condition
                                  (True - element is rendered; False - element is removed from Dom)
                                  Ex: <p v-if="isLoggedIn">Welcome</p>

                    v-else      - Alternative condition
                                  Ex: <p v-else>Please Login</p>

                    v-else-if   - Multiple conditions
                                  Ex: <p v-else-if="isPending">Loading...</p>

                    v-show      - Toggle visibility (display: none)
                                  Ex: <div v-show="isVisible">Content</div>

                    v-for       - List rendering
                                  Ex: <li v-for="item in items" :key="item.id">{{ item.name }}</li>

                    v-model     - Two-way data binding
                                  Ex: <input v-model="message" />

                    v-text      - Updates element's text content
                                  Ex: <span v-text="message"></span>

                    v-html      - Renders HTML content
                                  Ex: <div v-html="htmlContent"></div>

                Note: v-if removes element from DOM, v-show only hides it (CSS display: none)


8) Data Communication in Vue Js - In Vue.js, data communication happens using Props (Parent to Child), Emits (Child to Parent),
                                   Parent as mediator for siblings, Provide/Inject for deep nesting, and Vuex/Pinia for global state management.

                                | Method           | Direction          | Use Case                    |
                                | ---------------- | ------------------ | --------------------------- |
                                | Props            | Parent → Child     | Pass data down              |
                                | Emits ($emit)    | Child → Parent     | Send events up              |
                                | Parent Mediator  | Sibling ↔ Sibling  | Share data via parent       |
                                | Provide/Inject   | Ancestor → Deep    | Deep nesting (avoid props)  |
                                | Vuex/Pinia       | Global             | App-wide state management   |

    
  -->  Props - Data Flows From Parent to Child Communications.
               Data Flows downwards only.
              ex: 
                   <!-- Parent.vue -->
                      <template>
                          <ChildComponent :message="parentMessage" />
                        </template>
                        <script>
                          import ChildComponent from './ChildComponent.vue'
                              export default {
                                components: { ChildComponent },
                                data() {
                                  return {
                                    parentMessage: "Hello from Parent"
                                  }
                                }
                            }
                        </script>                  
                     <!-- Child.vue -->
                      <template>
                        <h2>{{ message }}</h2>
                      </template>
                      <script>
                          export default {
                            props: ['message']
                          }
                      </script>
 
                    o/p => Hello from Parent

  --> Emit Event ($emit) = Data Flows from Child to Parent Communications
                           Data Flows Upwarss using events.
                        ex: 
                            <!-- ChildComponent.vue -->
                            <template>
                              <button @click="sendData">Send to Parent</button>
                            </template>
                            <script>
                                export default {
                                  methods: {
                                    sendData() {
                                      this.$emit("updateMessage", "Hello from Child")
                                    }
                                  }
                                }
                            </script>
                             <!-- Parent.vue -->
                             <template>
                               <ChildComponent @updateMessage="handleUpdate" />
                              </template>
                             <script>
                                methods: {
                                  handleUpdate(data) {
                                    console.log(data)
                                  }
                                }
                             </script>

  --> Parent Mediator(Siblings - Siblings <-->Sibilings)

                          Sibling components communicate through the parent. 
                          One sibling emits an event to the parent,
                          the parent stores the data, and
                          then passes it to the other sibling using props.
                    
       Data Flow Diagram =  SiblingA  --(emit)-->  Parent  --(props)-->  SiblingB                        
                        ex:
                        <!-- Parent Component -->
                        <template>
                        <div>
                          <SiblingA @sendData="handleData" />
                          <SiblingB :message="sharedData" />
                        </div>
                      </template>
                      <script>
                        import SiblingA from './SiblingA.vue'
                        import SiblingB from './SiblingB.vue'
                          export default {
                            components: { SiblingA, SiblingB },
                            data() {
                              return {
                                sharedData: ''
                              }
                            },
                            methods: {
                              handleData(data) {
                                this.sharedData = data
                              }
                            }
                        }
                      </script>
                      <!-- Sibling A (Send Data) -->
                      <template>
                        <button @click="sendToParent">Send to Sibling B</button>
                      </template>
                      <script>
                        export default {
                          methods: {
                            sendToParent() {
                              this.$emit('sendData', 'Hello from Sibling A')
                            }
                          }
                        }
                      </script>
                      <!-- Sibling B (Receive Data) -->
                      <template>
                        <h3>{{ message }}</h3>
                      </template>
                      <script>
                        export default {
                          props: ['message']
                        }
                      </script>


  --> Provide & Inject (Deep Component Communication) - Used when components are deeply nested.
                   
                        It allows a parent component to send data to deeply nested child components

                        Note: Useful when avoiding prop drilling.
                              provide() is defined in script, NOT in template.
                              Template just renders child components normally.

                        App
                         └── Layout
                               └── Sidebar
                                     └── MenuItem

           Scenario -   If App has user data and MenuItem needs it:

                        Without provide/inject → You must pass props through every level ❌
                        With provide/inject → Direct access ✅
                  
                        Ex:
                            <!-- Parent Component (App.vue) Options Api -->
                            <template>
                              <Layout />  <!-- No props needed! -->
                            </template>

                            <script>
                            export default {
                              provide() {
                                return {
                                  username: "Amit",
                                  role: "Admin"
                                }
                              }
                            }
                            </script>

                            <!-- Deep Child Component (MenuItem.vue) -->
                            <template>
                              <h3>{{ username }} - {{ role }}</h3>
                            </template>

                            <script>
                            export default {
                              inject: ['username', 'role']  // Directly access provided data
                            }
                            </script>

                            How it works:
                            1. Parent defines provide() in script
                            2. Parent renders child components normally in template (no props)
                            3. Deep child uses inject to access provided data
                            4. Data flows invisibly through component tree


                          <!-- Composition API Version (Vue 3 Modern Way) -->

                              <!-- Parent.vue -->
                              <template>
                                <Layout />
                              </template>

                              <script setup>
                              import { provide, ref } from 'vue'
                              import Layout from './Layout.vue'

                              const username = ref("Amit")
                              const role = ref("Admin")

                              provide('username', username)
                              provide('role', role)
                              </script>

                              <!-- Child.vue -->
                              <template>
                                <h3>{{ username }} - {{ role }}</h3>
                              </template>

                              <script setup>
                              import { inject } from 'vue'

                              const username = inject('username')
                              const role = inject('role')
                              </script>

                              How it works (Composition API):
                              1. ref() makes data reactive
                              2. provide() shares reactive data down the tree
                              3. inject() receives the reactive reference
                              4. When parent changes username.value → child updates automatically ✅
                              5. Data remains reactive across all components
                  
                   Note - Provide/Inject is not reactive by default in Vue 2.
                          In Vue 3, if you provide a ref or reactive, it stays reactive.

                          So in modern Vue → Always provide ref() or reactive().

  
  --> Event Bus - Event Bus was used in Vue 2 for communication between unrelated components using a shared Vue instance.
                 In Vue 3, it is not recommended because it makes data flow unpredictable and harder to debug. Instead, 
                 we use Pinia / VueX for global state or parent-child communication patterns.

               - Event Bus was an old Pattern used in Vue 2 to allow communucation b/w unrelated components.  

               - Used for small applications (only for very small, specific use cases.)

               **What To Use Instead?**
                 
                 Parent Mediator
                 Provide / Inject (Deep nesting)
                 Global State Management (Best for large apps)

                 Ex: 

                      Step 1: Create Event Bus
                      
                        // eventBus.js
                        import Vue from 'vue'
                        export const eventBus = new Vue()

                      Step 2: Emit Event (Component A)

                        <script>
                        import { eventBus } from './eventBus'

                        export default {
                          methods: {
                            sendData() {
                              eventBus.$emit('sendMessage', 'Hello')
                            }
                          }
                        }
                        </script>

                      Step 3: Listen to Event (Component B)

                        <script>
                        import { eventBus } from './eventBus'

                        export default {
                          created() {
                            eventBus.$on('sendMessage', (data) => {
                              console.log(data)  // "Hello"
                            })
                          },
                          beforeUnmount() {
                            eventBus.$off('sendMessage')  // Clean up!
                          }
                        }
                        </script>

                      Note: Always remove listeners in beforeUnmount to prevent memory leaks!

               Note - Why It’s NOT Recommended in Vue 3?

                      ❌ $on, $off, $once were removed

                      ❌ Hard to track data flow

                      ❌ Makes debugging difficult

                      ❌ Causes memory leaks if listeners aren’t removed

                      ❌ Breaks predictable state management

               Note - Vue 3 removed this pattern intentionally.

               Can We Still Use Event Bus in Vue 3?

                Yes, but using external library like:

                mitt (small event emitter library)

              Ex:
                  import mitt from 'mitt'
                  export const emitter = mitt()
              
              Note: only for very small, specific use cases.


9) Global Component = A global component in Vue is a reusable component registered once and available throughout the application without importing it everywhere.

                    Ex: 
                        Common UI like:

                             -> Button

                             -> Input

                             -> Navbar

                             -> Loader

                             -> Modal

                             -> Footer
            
            Note: global components are registered in main.js or main.ts.


           ** When NOT to Use Global Components

              Component is used in only one place

              Large components (affects performance)

              Makes project harder to maintain

            Note:- Use global components only for base UI components (BaseButton, BaseInput, BaseCard).

            Ex:

                <!-- Step 1: Create Component (BaseButton.vue) -->
                <template>
                  <button class="btn">{{ label }}</button>
                </template>

                <script>
                export default {
                  props: ['label']
                }
                </script>

                <!-- Step 2: Register Globally (main.js) -->
                import { createApp } from 'vue'
                import App from './App.vue'
                import BaseButton from './components/BaseButton.vue'

                const app = createApp(App)
                app.component('BaseButton', BaseButton)  // Register globally
                app.mount('#app')

                <!-- Step 3: Use Anywhere (No Import Needed!) -->
                <template>
                  <div>
                    <BaseButton label="Click Me" />
                    <BaseButton label="Submit" />
                  </div>
                </template>

                <!-- No import needed! BaseButton is available everywhere ✅ -->

 10) Slot = A Slot is a placeholder inside a component that allows the parent to pass custom content into it.

            Types of Slots:

                1. Default Slot - Basic slot for simple content insertion.

                2. Named Slot - Multiple slots with specific names for different content areas.

                3. Scoped Slot - A slot that allows the child component to pass data back to the parent.

            Ex:

                <!-- Parent.vue -->
                <template>
                  <Card>
                    <template #header>
                      <h2>Card Header</h2>
                    </template>

                    <p>This is the main content of the card.</p>

                    <template #footer>
                      <button>Card Footer Button</button>
                    </template>
                  </Card>
                </template>

                <!-- Card.vue -->
                <template>
                  <div class="card">
                    <div class="card-header">
                      <slot name="header"></slot>  <!-- Named Slot for Header -->
                    </div>

                    <div class="card-body">
                      <slot></slot>  <!-- Default Slot for Main Content -->
                    </div>

                    <div class="card-footer">
                      <slot name="footer"></slot>  <!-- Named Slot for Footer -->
                    </div>
                  </div>
                </template>


 11) Scope = Scope in Vue defines where data, styles, or variables can be accessed — inside a component, across components, or globally.

            Types of Scope:

                1. Component Scope (Local) - Data and methods are accessible only within that component.

                2. Slot Scope - data passed from child to parent.

                3. Global Scope - Data or components accessible throughout the entire app.

                4. Styles Scope - CSS styles apply only to the current component.

            Ex:

                1. Component Scope (Local)

                    <template>
                      <p>{{ message }}</p>
                    </template>

                    <script>
                    export default {
                      data() {
                        return {
                          message: "Hello"  // Only accessible in this component
                        }
                      }
                    }
                    </script>

                 2. Slot Scope

                    <!-- Child.vue -->
                    <template>
                      <slot :user="user"></slot>
                    </template>

                    <script>
                    export default {
                      data() {
                        return {
                          user: { name: "Amit" }
                        }
                      }
                    }
                    </script>

                    <!-- Parent.vue -->
                    <template>
                      <ChildComponent>
                        <template #default="slotProps">
                          {{ slotProps.user.name }}
                        </template>
                      </ChildComponent>
                    </template>
                
                    Note: user belongs to child
                          Parent can access it using slot scope

                 3. Global Scope

                    // main.js
                    app.component('BaseButton', BaseButton)
                    
                    <!-- Accessible everywhere without import -->
                    <template>
                      <BaseButton />
                    </template>
                 
                    Note: Global variables, global components, global plugins → available across the app.

                 4. Scoped Styles 
                <style scoped>
                .card {
                  background: white;  /* Only applies to this component */
                }
                </style>
              
              Note: Styles apply only to this component
                    Won’t affect other components
              
              Note: Without scoped, styles become global.

 
 12) Vue Loader = Vue Loader is a tool that allows you to use Single File Components (.vue files) in projects that use Webpack.
                Note : It converts .vue files into normal JavaScript modules that the browser can understand.
                A .vue file looks like this:
                <template>
                  <div>Hello</div>
                </template>
                <script>
                  export default {
                    name: "HelloComponent"
                  }
                </script>
                <style scoped>
                  div {
                    color: red;
                  }
                </style>

      Note: But browsers don’t understand .vue files directly ❌

                  So Vue Loader:

                  Separates <template>, <script>, and <style>

                  Compiles template into render function

                  Processes scoped CSS

                  Sends final JS to Webpack

                  Webpack bundles everything

     Note: What Vue Loader Does Internally

            When using Webpack:

                    {
                      test: /\.vue$/,
                      loader: 'vue-loader'
                    }

          ==> Vue Loader:

                  Parses the .vue file

                  Compiles template → JavaScript

                  Applies CSS scoping

                  Supports preprocessors (SCSS, TypeScript, etc.)

                  Exports component as JS module

            
            Note: Vite does NOT use Vue Loader.
                  It uses a plugin: @vitejs/plugin-vue.

                  | Tool    | Uses       |
                  | ------- | ---------- |
                  | Webpack | Vue Loader |
                  | Vite    | Vue Plugin |


 13) VUE-Router = It allows us to navigate between different pages (components) in a Single Page Application (SPA) without reloading the page.

                How It works ? 
                   
                    - User clicks a link
                    - URL changes
                    - Vue Router loads the corresponding component
                    - Page updates without full refresh

                Ex: 
                      // router/index.js
                      import { createRouter, createWebHistory } from 'vue-router'
                      import Home from '../views/Home.vue'
                      import About from '../views/About.vue'

                      const routes = [
                        { path: '/', component: Home },
                        { path: '/about', component: About }
                      ]

                      const router = createRouter({
                        history: createWebHistory(),
                        routes
                      })

                      export default router

                      main.js:
                      import router from './router'
                      app.use(router)

14) Navigation Gaurd = Navigation Guard is a feature from Vue Router that allows you to control or restrict route navigation.

                       Common real-time scenarios: 

                                      - Protect dashboard pages (only logged-in users)
                                      - Redirect users if not authorized
                                      - Prevent leaving a form with unsaved data
                                      - Role-based routing (Admin / User)

                       Note: It is mainly used for authentication, authorization, and preventing unauthorized page access.
                      
                       Types of Navigation Guards : 

                                      - Global Guards
                                      - Route-Level Guards
                                      - Component-Level Guards

                          Ex: 
                              {
                                path: '/dashboard',
                                component: Dashboard,
                                meta: { requiresAuth: true }
                              }

                              router.beforeEach((to) => {
                                if (to.meta.requiresAuth && !localStorage.getItem('token')) {
                                  return '/login'
                                }
                              });


15) History Modes in Vue Router =  Vue Router supports different ways to manage URLs.

                                Mainly:

                                  1️⃣ Hash Mode - https://example.com/#/about

                                  2️⃣ HTML5 History Mode  - https://example.com/about  (Clean URL)
                                
                                  3️⃣ Memory Mode (mostly SSR) - Used in server-side rendering environments.

                  Note : If the application is deployed on a server without proper configuration, I would recommend hash mode.
                         But for SEO-friendly production apps, history mode is preferred


16) Lazy Loading = Lazy loading in Vue means loading components only when they are needed using dynamic imports.
                   It improves performance by reducing the initial bundle size. It is mostly used with Vue Router,
                   where route components are loaded only when the user navigates to that route.

                  Ex:  

                      const routes = [
                          { path: '/', component: () => import('../views/Home.vue') },
                          { path: '/about', component: () => import('../views/About.vue') },
                          { path: '/dashboard', component: () => import('../views/Dashboard.vue') }
                        ]

                    
                    Note: Lazy loading is mostly used in routing.
