# Level 2: Intermediate (real usage)

Remove value 30 from [10, 20, 30, 40] immutably . //Slice() + spread(...) - immutable

 Solutions : 
                const number = [10,20,30,40];
                    const remove = [
                    ...number.slice(0,2),
                    ...number.slice(3)
                    ];
                console.log(remove);
                <!-- [ 10, 20, 40 ] -->
                
<!-- Slice() adds / removes the elements from the middle element -->

Insert 25 at index 2 in [10, 20, 30, 40].

 Solutions : 
                const number = [10, 20, 30, 40];
                const insert = [
                    ...number.slice(0,2),
                    25,
                    ...number.slice(2),
                ];
                console.log(insert)
                <!-- [ 10, 20, 25, 30, 40 ] -->

Sort [3, 1, 10, 2] in ascending order.***

 Solutions :             
              const array = [3, 1, 10, 2];
              const ascending = array.sort( (a,b) => a-b );
              console.log(ascending)
              <!-- [ 1, 2, 3, 10 ] -->

Sort an array of objects by age.

 Solutions : 
            const users = [
                { name: "Amit", age: 30 },
                { name: "Neha", age: 25 },
                { name: "Rahul", age: 35 }
            ];
        users.sort((a, b) => a.age - b.age);
        console.log(users)        
        <!-- 
            [
                { name: 'Neha', age: 25 },
                { name: 'Amit', age: 30 },
                { name: 'Rahul', age: 35 }
            ] 
        -->

Get only even numbers from [1,2,3,4,5,6].

Find the first number greater than 50.

Convert ["a", "b", "c"] to ["A", "B", "C"].

 Solutions : 
             const alpha = ["a", "b", "c"];
             const upperCase = alpha.map(char => char.toUpperCase() );  
             console.log(upperCase)
        <!-- [ 'A', 'B', 'C' ] -->
        <!-- maP() - iterates the array element & Returns new Array -->
        <!-- map() is used to transform each element of an array and return a new array. -->
 
Merge [1,2] and [3,4] without mutating.
 
 Solutions : 
             const a = [1,2];
             const b = [3,4];
             const merge = a.concat(b);
             console.log(merge)
            <!-- [ 1, 2, 3, 4 ] -->
    <!-- Concat() - Immutable - merges the array -->