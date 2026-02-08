 
 # Array Destructuring
 
 array destructring  : Array destructuring is a JavaScript feature that allows you to extract values from an array
                         and assign them to variables in a single, concise syntax, based on their position (index) in the array.                            
                            ex: 
                            
                            Removing the Duplicate Numbers

                                const numbers = [1,2,3,4,2,5,6,2];
                                const unique = [...new Set(numbers)];

                                console.log(unique)

                                o/p - [ 1, 2, 3, 4, 5, 6 ]

                            Rest Operator: -

                                const arr = [1, 2, 3, 4, 5];
                                const [first, second, ...rest] = arr;

                                console.log(first);  // 1
                                console.log(second); // 2
                                console.log(rest);   // [3, 4, 5]


                            Swap Variables -

                                let a = 1;
                                let b = 2;
            
                                [a, b] = [b, a];

                                console.log(a); // 2
                                console.log(b); // 1

        
    Note: Array destructuring depends on order

          Object destructuring depends on property names.

          Syntax: - Uses [] ;  array; Uses {}
          Common use - Lists, function returns ; Configs, API responses
          Variable naming - Any name ; Must match property name (or use alias)


    Object Destructring : Object destructuring extracts values using property names, not position.

                        ex: 

                           const person = {
                            name: "Amit",
                            age: 30
                            };

                            const { name, age } = person;
                            console.log(name, age);

                            // object destructring 