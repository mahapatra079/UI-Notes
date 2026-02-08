# Array Methods - An array is a fundamental data structure that stores a collection of elements.

1) push() – add at end

            Ex: 
                    const arr = [1, 2];
                    arr.push(3);

                    console.log(arr); // [1, 2, 3]

2) pop() - remove from end

            ex:
                    const arr = [1, 2, 3];
                    arr.pop();

                    console.log(arr); // [1, 2]

3) unshift() – add at start

            ex: 
                    const arr = [2, 3];
                    arr.unshift(1);

                    console.log(arr); // [1, 2, 3]

4) shift() – remove from start
            
            ex:                                      
                    const arr = [1, 2, 3];
                    arr.shift();

                    console.log(arr); // [2, 3]

5) Add / Remove the elements in the Middle

    Note: splice() can add or remove elements at any position by mutating the array, while
          slice() is used with the spread operator to add elements  immutably at any position

    ex: Slice

        let arr = [10, 20, 40, 50];

        // add 30 at index 2
        arr.splice(2, 0, 30);

        console.log(arr);
        // [10, 20, 30, 40, 50]


    ex: - Slice + spread operator

        let arr = [10, 20, 40, 50];

        let newArr = [
        ...arr.slice(0, 2), // before
        30,                 // add anywhere
        ...arr.slice(2)     // after
        ];

        console.log(newArr);
        // [10, 20, 30, 40, 50]


        filter → remove values

                ex: - 
                        let arr = [10, 20, 30, 40, 50];

                        let removedArr = arr.filter(item => item !== 30);
                        console.log(removedArr);
                        // [10, 20, 40, 50]
        
    note: To remove an element immutably from the middle of an array, we use slice() with the spread operator or filter().

# Difference  B/W Splice & Filter: -

    Both splice and filter are O(n), but splice is faster when the index is known because it mutates the array and only shifts elements after that index, while filter always iterates the entire array and creates a new one. In React, filter is preferred due to immutability.

    Summary:- splice = faster, mutating, index-based
                filter = safer, immutable, value-based
    
    O(n) - The time taken by an algorithm grows linearly with the number of elements n.
            Ex:
                arr = [10, 20, 30, 40, 50] // n = 5
                If you need to look at each element once, that’s O(n).                            
               

# Mutable vs Immutable

    Mutable - Data can be changed after creation
            
            ex: 
                push()
                pop()
                shift()
                unshift()
                splice()
                sort()
                reverse()


    Immutable - Data cannot be changed; you create a new copy
            
            Ex : 
                
                concat()
                slice()
                filter()
                map()
                reduce()                  

Note: Mutable data can be changed directly, while immutable data cannot be modified and instead returns a new copy.
      JavaScript arrays and objects are mutable by default, but in React we follow immutability to ensure predictable state updates and proper re-rendering.


Concat - concat() is an immutable array method used to merge arrays or add elements and returns a new array.

        Syntax: array1.concat(array2, value1, value2, ...)

        Ex:
            let a = [1, 2];
            let b = [3, 4];

            let result = a.concat(b);

            console.log(result);
            // [1, 2, 3, 4]
         <!-- Retruns New Array -->



 map() → change values / is used for list rendering

        ex: 
            JS Version

                const users = [1,2,3,4,5,6,7,8,9]

                const userList =users.map(user => `${user}`)
                console.log(userList)
                o/p - [ '1', '2', '3', '4', '5', '6', '7', '8', '9' ]
 
        => This return new Array

        React Version

               let users = ["Amit", "Rahul", "Neha"];

                return (
                <ul>
                    {users.map(name => (
                       <li key={name}>{name}</li>
                    ))}
                </ul>
                );

      Vue Version        
                <template>
                    <ul>
                        <li v-for="user in users" :key="user">{{ user }}</li>
                    </ul>
                </template>



 forEach() - is used to loop through each element of an array

        ex:                                            
            const numbers = [1, 2, 3];

            numbers.forEach(num => {
                console.log(num);
            }); 

        => No return value with array = 1 2 3 

 for loop - A for loop is used to run a block of code multiple times based on a condition.

        ex:                                            
            const nums = [10, 20, 30];

            for (let i = 0; i < nums.length; i++) {
            console.log(nums[i]);
            }


 Sort() / Reverse() :-

    Sort() - Arrange the elments

            Ex:
                let arr = [3, 1, 10, 2];

                arr.sort();

                console.log(arr);
                // [1, 10, 2, 3] 

                Ascending:- 

            Ex: let arr = [3, 1, 10, 2];

                arr.sort((a, b) => a - b);

                console.log(arr);
                // [1, 2, 3, 10]
            
                Descending:-

                Ex: arr.sort((a, b) => b - a);
    
    Reverse() - reverses the array elements

            Ex: 
               let arr = [1, 2, 3];
  
               arr.reverse();
 
               console.log(arr);
               // [3, 2, 1]

    Note: - 🔹 sort() + reverse() combo
            
            Ex: let desc = [...arr].sort((a, b) => a - b).reverse();



 reduce → combine values / is used to combine array elements into a single value.

            Ex: 
                
                const numbers = [1, 2, 3, 4];

                const sum = numbers.reduce((total, num) => total + num, 0);

                console.log(sum); // 10

                o/p - 10


 2) includes() / indexOf() / find(): Methods for checking the presence or location of elements


        includes() - Returns Boolean (true / false) (Is it present?)

                    Ex: 
                        let arr = [10, 20, 30];

                        arr.includes(20); // true
                        arr.includes(40); // false

                 Note: Can check NaN (important!)
                       ex: [NaN].includes(NaN); // true


        indexOf() - where is it ( returns the position - index / -1 )
                    
                    Ex: 
                        let arr = [10, 20, 30];

                        arr.indexOf(20); // 1
                        arr.indexOf(40); // -1
                 
                 Note: Does NOT work with NaN
                       Ex: [NaN].indexOf(NaN); // -1
        
        find() - Give me the element (Returns the element / undefined)

                   ex: 
                        let arr = [10, 20, 30];

                        let result = arr.find(x => x > 15);
                        
                        <!-- with Array -->

                        console.log(result);
                        // 20

                    Ex: 
                        let users = [
                            { id: 1, name: "Amit" },
                            { id: 2, name: "Neha" }
                            ];

                            let user = users.find(u => u.id === 2);

                            <!-- With Objects -->

                            console.log(user);
                            // { id: 2, name: "Neha" }


        | Method       | Returns                |
        | ------------ | ---------------------- |
        | `includes()` | `true / false`         |
        | `indexOf()`  | index or `-1`          |
        | `find()`     | element or `undefined` |


 Note: flat(): Creates a new array with all sub-array elements concatenated into it recursively up to a specified depth.
               
 Note: Array.isArray(): A static method to determine if a passed value is an Array.

 How do you check if a variable is truly an array?

 Use Array.isArray(value). Using typeof will return 'object'.   

          

 3) Spread Operator(...): - The spread operator expands (spreads) elements of an array, object, or iterable into individual values.

                    Ex: 
                        let arr = [1, 2, 3];
                        let copy = [...arr];

                            <!-- Array Values -->

                        console.log(copy); // [1, 2, 3]

                    
                    Ex: 
                        let user = { name: "Amit", age: 28 };
                        let updatedUser = { ...user, age: 29 };

                        <!-- Object Value -->

                        console.log(updatedUser);
                        // { name: "Amit", age: 29 }

