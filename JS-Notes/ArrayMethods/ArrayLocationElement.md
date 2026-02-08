# Array Methods - For Checking the presence or location of an elements. 

 includes() / indexOf() / find(): Methods for checking the presence or location of elements


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