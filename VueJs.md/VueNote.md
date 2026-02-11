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
                   
                 - It allows a parent component to send data to deeply nested child components

                  Note - Useful when avoiding prop drilling.

                           

