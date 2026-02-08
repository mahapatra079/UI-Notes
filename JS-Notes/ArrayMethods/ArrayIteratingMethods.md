# Array - Multiple ways to Iterate over an array 

**ForLoop**
**ForEach**

**map**
**filter**
**reduce**

**for...in**
**for...of**
**while / do...while**


for loop - A for loop is used to execute a block of code multiple times based on a given condition.

    ex:                                            
        const nums = [10, 20, 30];

        for (let i = 0; i < nums.length; i++) {
          console.log(nums[i]);
        }

        o/p => 10
               20
               30

    Note: Since nums.length is 3, the loop runs 3 times.

    Flow - 
            i = 0 → prints 10
            
            i = 1 → prints 20

            i = 2 → prints 30

            i = 3 → condition fails → loop stops


forEach() - iterates over an array and executes a function for each element, but it does not return a new array.

        ex:                                            
            const numbers = [1, 2, 3];

            numbers.forEach(num => {
                console.log(num);
            }); 

        => No return value with array = 1 2 3 


 map() → is used to change/transform values in an array and is commonly used for list rendering in UI frameworks like React.

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


 filter → remove values

                ex: - 
                        let arr = [10, 20, 30, 40, 50];

                        let removedArr = arr.filter(item => item !== 30);
                        console.log(removedArr);
                        // [10, 20, 40, 50]
        
 note: To remove an element immutably from the middle of an array, we use slice() with the spread operator or filter().


 reduce → combine values / is used to combine array elements into a single value.

            Ex: 
                
                const numbers = [1, 2, 3, 4];

                const sum = numbers.reduce((total, num) => total + num, 0);

                console.log(sum); // 10

                o/p - 10


 for...in Loop - is used to iterate over the keys (indexes) of an object or array. 

        Ex: **Array**

            const nums = [10, 20, 30];
               for (let index in nums) {
               console.log(index, nums[index]);
            }


        o/p => 0 10
               1 20
               2 30

        
        Ex:**Object**

                const user = {
                    name: "Amit",
                    age: 30
                  };

                for (let key in user) {
                  console.log(key, user[key]);
                }

        o/p =>
                name Amit
                age 30 
           

 Note: Iterates over indexes/keys, not values
       Indexes are returned as strings

       map() works only on arrays
      const name = user.map(person => person); // ERROR

       user is an object
       Objects do not have map()



**map() works only on arrays, then how do we map objects in React?**

**We don’t map objects directly.**
**We convert objects to arrays first, then use map()**

# Case 1: Object → list rendering (most common)
    const users = {
        1: { name: "Amit", age: 30 },
        2: { name: "Neha", age: 25 }
    };

 **Convert to array + map (React way)**
        <ul>
        {Object.values(users).map((user, index) => (
            <li key={index}>
              {user.name} - {user.age}
            </li>
        ))}
        </ul>

 Note: Object.values() → array
       map() → JSX rendering

# Case 2: You need keys + values (IDs)

    <ul>
        {Object.entries(users).map(([id, user]) => (
            <li key={id}>
            {user.name} - {user.age}
            </li>
        ))}
    </ul>

 Note: Best when ID is important
       Avoids using index as key

# Case 3: Object inside array (VERY common)

    const users = [
        { name: "Amit", age: 30 },
        { name: "Neha", age: 25 }
     ];

     <ul>
        {users.map(user => (
            <li key={user.name}>{user.name}</li>
        ))}
     </ul>

  Note: outer structure is an array


 Note : React maps arrays, not objects.
        Objects must be converted using Object.values() or Object.entries().

 
 **React uses map() on arrays; objects are converted to arrays first**

 **map() works on arrays only**
 **Objects must be converted to arrays first using**
 **Object.keys(), Object.values(), or Object.entries()**
