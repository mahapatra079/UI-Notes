  # javascript: JavaScript is a programming language and core technology of the Web Browser, alongside HTML and CSS.

  1) Hoisting ******
  2) promise ****
  3) async/await ***
  4) event loop **
  5) Array Methods **
  6) Sorting **
  7) array destructring  / object destructring **
  8) Closure **
  9) this *
  10) setTimeout vs setInterval **
  11) debouncing and throttling *
  12) let vs var vs const *****
  13) == vs === *
  14) single Thread vs multi Thread *
  15) JS Vs Typescript
  16) map vs filter vs reduce  / (forEach() - for loop )
  17) Js Debugging application **
  18) js Object types - dom / bom / event object ....
  19) Rest Api call / Service call
  20) Deployment Process - jenkins / docker  **
  21) pass by Value / pass by refernce
  22) Asynchronous
  23) Polyfills
  24) Prototype
  25) Event Bubbling? how would you stop?


 1) Event Loop: Responsible for managing the execution of code, collecting and processing events.
                It continuously monitors the call stack and various queues.., ensuring smooth performance,
                and maintaining application responsiveness. 

                JS is a Single Thread 
                Heap - used for amemory allocation
                Stack - Stack hold the execution context


     Call Stack: A LIFO (Last-In, First-Out) data structure where synchronous code is executed. When a function is called,
                 it is pushed onto the stack, and when it returns, it is popped off.
    
     Time Queues: This callbacks  are executed in FIFO order  / (not technically time queues ...... Heap data structure)

     I/O Queue - fs.readFile()

         Ex:    const fs = require("fs");

                fs.readFile(__filename, () => {
                console.log("this read file 3");
                });

                process.nextTick(() =>
                console.log("This is process next tick 1")
                );     console.log("A");

                setTimeout(() => {
                console.log("B");
                }, 1000);

                console.log("C");


                Promise.resolve().then(() =>
                console.log("This is promise resolve 2")
                );

           Note: Use setImmediate instead of fs.readFile to simulate I/O
                 Using too many process.nextTick calls can starve the event loop and delay I/O like fs.readFile.


     I/O Plling - 

        Task Queues (Macrotask Queue): This queue holds callbacks for events like timers (setTimeout, setInterval), user interactions (clicks), and network requests that have completed.  
    
        Microtask Queue: This queue has a higher priority than the task queue and holds callbacks for Promises (.then(), .catch(), .finally()) and queueMicrotask().
        
        ex: 
            
                console.log("1");
                process.nextTick(()=> console.log("this process is nect tick 1"));
                console.log("2")

                Call stack:
                    console.log("1")
                    console.log("2")

                Next Tick Queue:
                    process.nextTick callback
        
        Note: Too many process.nextTick calls can block the event loop
        Note: JavaScript always finishes the current call stack before touching async queues.


        Promise.resolve().then(() => console.log("this promise to be resolved as 1"));
        process.nextTick(() => console.log ("this process next tick is 2"));


        // process.nextTick beats Promises.
        // Promises beat timers.


     setTimeout callback is a macrotask and runs in a subsequent event loop cycle. 


         Ex:
                console.log("A");

                setTimeout(() => {
                console.log("B");
                }, 1000);

                console.log("C");

             Output

                A
                C
                B
                
             Because setTimeout waits, while JS keeps going.


             2md Scenario

             console.log("A");   

             <!-- runs immediately -->
 
             setTimeout(() => {
              console.log("B");
             }, []);
                <!-- 
                    setTimeout(...)
                    The [] is converted to 0
                    So this becomes: setTimeout(fn, 0)
                    The callback is scheduled, not run now
                -->

             console.log("C");

             <!-- runs immediately -->


 Flow :  Event Loop Flow 

            Synchronous code
                 ↓
            process.nextTick
                 ↓
            Promise.then / queueMicrotask
                 ↓
            I/O callbacks (fs, net, etc.)
                 ↓
            setImmediate
                 ↓
            setTimeout / setInterval


        Note: Execution order is not guaranteed because JavaScript does NOT control when async work finishes.
              The OS, thread pool, and event loop do.

 2) setTimeout vs setInterval - 
         
          setTimeout - Runs a function one time after a delay.

               ex: 
                setTimeout(() => {
                console.log("Hello after 2 seconds");
                }, 2000); 

        Note: Can be canceled with clearTimeout

        setInterval - Runs a function repeatedly at fixed intervals.
                    
                    ex: 

                        setInterval(() => {
                        console.log("Runs every 2 seconds");
                        }, 2000);
                        
        Note : Can be stopped with clearInterval


 3) Promise - It represent an asynchronous options in which the subscriber notifies the handlers whether to resolve  or reject.
              
              Syntax:
                        const promise = new Promise((resolve, reject) => {
                            
                                 // async work
                         
                          });

             Ex: 
                   const promise = new Promise((resolve, reject) => {
                        setTimeout(() => {
                            resolve("done"); // or reject(error)
                        }, 1000);
                        });
            
             Promise chaining:

                        fetch(url)
                            .then(res => res.json())
                            .then(data => process(data))
                            .catch(err => handle(err)); - .catch() runs ONLY when the promise is rejected
                    
                    ex : 
                         
                          promise.then(value => {
                            console.log(value);
                            });

                    Note: Similarly for catch, finally (Consuming promise)

             Promise states : 

                    pending – initial state
                            
                            ex:
                                const promise = new Promise((resolve,reject)=>{

                                    <!--
                                        JS checks the Promise immediately, but:

                                            No resolution has occurred

                                            No rejection has occurred 
                                    
                                    -->                                               

                                    });
                                console.log(promise);

                        o/p - <!-- Promise { <pending> } -->

                    fulfilled – resolved successfully
                            
                            ex: 

                                    const promise = new Promise((resolve, reject) => {

                                    setTimeout(() => resolve("success"), 1000);
                                        
                                    });
                                    
                                    console.log(promise); 

                                    promise.then(value => {
                                    
                                    console.log(value);
                                    
                                    });

                            o/P - Promise { <pending> } 
                                success

                    rejected – failed

                    ex: const promise = new Promise((resolve, reject) => {
                        setTimeout(() => {
                            reject("failed");
                        }, 1000);
                        });

                        console.log(promise);

                        promise.then(result => {
                            console.log(result); // ❌ will NOT run
                        })
                            .catch(error => {
                            console.log(error); // ✅ "failed"
                        });

                    o/p - Promise { <pending> }
                            failed
                    
                    Note: Any error thrown inside a Promise automatically becomes a rejection - (reject, throw Error - [.catch()])

 4) async/await -      
                 - aysnc functions return a Promise 

                 - await wait for Promise result inside async function

                 ex:
                    
                     function getData() {
                        return new Promise(resolve => {
                            setTimeout(() => {
                            resolve("Data received");                             
                            }, 1000);
                            //   Runs a function one min after a delay 
                        });
                        }

                        async function showData() {
                        const result = await getData();

                            // getData() returns a Promise
                            // await waits until the Promise resolves  

                        console.log(result);
                        }

                        showData();

                        // After 1 second → "Data received" is logged   


 5) Hoisting - Hoisting is JS behaviour where variables & functions decalarations are moved to the top of 
               there scope before the code execeution.
            
         Ex:    
                 function greet(){
                    console.log("good morning");
                    }

                    greet();
                 <!-- fully-hoisted -->


                    var greet = function greet(){
                        console.log("good morning");
                    }
                    greet();
                 <!-- fully-hoisted -->



                 var greet;          // hoisted
                 greet();            // ❌ greet is undefined 

                  var greet = function greet(){
                    console.log("good morning");
                  }


            Note: Function declarations are hoisted with body
                  Function expressions are NOT
                 
                 
                  var greet = function greet() {}

            Note: This is a function expression, NOT a function declaration.      


 6) Closure - A closure in JavaScript is a function that remembers and has access to variables from its outer scope,
              even after the outer function has finished executing.

    ex: 
        
         function outer() {
            let count = 0;

            function inner() {
                count++;
                console.log(count);
            }

            return inner;
            }

            const increment = outer();

            increment(); // 1
            increment(); // 2
            increment(); // 3

        The function inner() forms a closure by retaining access to outerVar, which is a variable in the scope of outer().
        Even though outer() has completed execution, inner() still has access to outerVar due to the closure.

     What’s happening?

        outer() runs and returns inner

        Normally, count should be gone after outer() finishes

        But inner() keeps a reference to count

        That persistent reference = closure

  
     when JS needs a variable, it looks in this order:

            1️⃣ Local scope
            2️⃣ Parent (lexical) scope
            3️⃣ Global scope
            4️⃣ ReferenceError

 7) This  - this keyword refers to the object that is executing the current function.

            ex:
            
                const person = {
                    name: "GeeksforGeeks",
                    greet() {
                        return `Welcome To, ${this.name}`;
                    }
                };
                console.log(person.greet());debouncing

                2nd scenario 
                
                function Car(brand) {
                this.brand = brand;
                }
                const myCar = new Car("Toyota"); // 'this' refers to the new Car object


 8) debouncing and throttling 

        
            | Debounce                  | Throttle              |
            | ------------------------- | --------------------- |
            | Runs **after** user stops | Runs **at intervals** |
            | Delays execution          | Limits execution      |
            | Search input              | Scroll / resize       |

        
            Debounce  When to use Debounce

                        ✔ Search input
                        ✔ Resize event
                        ✔ Auto-save drafts       

            Trottle -  When to use Throttle

                        ✔ Scroll events
                        ✔ Button spam prevention
                        ✔ Window resize tracking


 9) Js debugging -  I debug JavaScript using browser DevTools. I use console.log and debugger for quick checks,
                     set breakpoints in the Sources tab to inspect variables and execution flow,
                     and use the Network tab to debug API calls. For UI frameworks like React,
                     I also use React DevTools to inspect state and props.


                    ex:   
                        1)  * console.log()
                        
                              console.log("User data:", user);

                         note: Print values and see what’s going on. 
                               Log before & after a function call to trace flow.

                        2) Using debugger keyword (super powerful) - This pauses execution exactly like a breakpoint.


                                ex: 
                                    function calculateTotal(price) {
                                        debugger;
                                        return price * 1.18;
                                    }

                            When DevTools is open → code stops at debugger and you can:

                                        Inspect variables

                                        Step over / into code

                                        Check call stack


                        Note: Browser DevTools - (Chrome / Edge / Firefox); 
                              Breakpoints (real debugging)  


10) == vs === :-

 == (Loose equality): - Compares values only                       
                        Does type conversion (type coercion) before comparing

                        Ex:  
                            5 == "5"   // true
                            true == 1  // true
                            null == undefined // true
                            [] == false  //true
                            [] == ![] // true
                            Number.isNaN(NaN) // true
                            NaN == NaN // false
                            0 == ""  //true
                            false == "" //true
                            {} == {} // fasle
                            [] == [] //false

 === (Strict equality):- Compares both value AND type
                         No type conversion

                        ex:
                            5 === "5"  // false
                            true === 1 // false
                            null === undefined // false
                            "0" === false // false
                            NaN === NaN // false
                            0 === "" // false


11) Pass By Value vs Pass By Reference - 

                  - In JavaScript, primitive values are passed by value, which means a copy is created.
        
                  - Objects are passed by reference value, which means the reference is copied, so changes to object properties 
                    inside a function affect the original object.


    
    Pass By Value - When passed to a function, a copy is created.

                    Primitive types: Primitive types → Pass by Value

                            number

                            string

                            boolean

                            null

                            undefined

                            symbol

                            bigint
                    
          Ex : - 
                      
                 function updateValue(x) {
                      x = 20;
                      console.log("Inside:", x);
                }

                let a = 10;
                updateValue(a);
                console.log("Outside:", a);

            o/p - Inside: 20
                  Outside: 10
        
            Why?
                Because a was copied.
                Changing x does NOT affect a.


    Objects → Pass by Reference (actually pass by reference value)

                Objects:
                            Arrays

                            Objects

                            Functions
            
        
               Note : The reference (address) is copied, not the actual object.

               ex:  

                   function updateObject(obj) {
                        obj.name = "Amit";
                    }

                    let person = { name: "John" };

                    updateObject(person);
                    console.log(person.name);

                why ?

                Because both person and obj point to the same memory location.

        
        | Feature                        | Pass by Value  | Pass by Reference              |
        | ------------------------------ | -------------  | -----------------------------  |
        | Data Type                      | Primitive      | Object                         |
        | Memory                         | Copy created   | Reference copied               |
        | Changes affect original?       | No             | Yes (if modifying property)    |
        | Reassignment affects original? | No             | No                             |


