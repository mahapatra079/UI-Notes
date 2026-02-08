# Level 1: Basics (warm-up)

Add an element to the end of an array.

Solutions :
            const array = [1,2,3]
            array.push(4); 
            console.log(array) 
            <!-- [ 1, 2, 3, 4 ] -->

Remove the last element from an array.

 Solutions :
          const array = [1,2,3]
          array.pop(); 
          console.log(array)
          <!-- [ 1, 2 ] -->

Add an element to the start of an array.

Solutions : 
            const array = [2,3,4,5]
            array.unshift(1);
            console.log(array)
            <!-- [ 1, 2, 3, 4, 5 ] -->

Remove the first element from an array.

 Solutions : 
            const array = [2,3,4,5]
            array.shift();
            console.log(array)
            <!-- [ 3, 4, 5 ] -->

Check if value 10 exists in [5, 10, 15].

 Solutions :
            const array = [5, 10, 15];
            const result = array.includes(10); 
            <!-- includes() returns a boolean -->
            console.log(result);
            <!-- returns True  -->

  // includes() checks whether the element is present and returns true or false


Find the index of "apple" in ["banana", "apple", "orange"].

 Solutions : 
             const fruits = ["banana", "apple", "orange"];
             const index = fruits.indexOf("apple"); 
             console.log(index) 
          <!-- indexOf() - returns the index (position) of an element -->
             o/p => 1  
          <!-- It returns the position (index) -->                       
 
Reverse an array without mutating the original array.
 Solutions : 
              const array = [1,2,3,4,5];
              const reversed = [...array].reverse() //immutable
              console.log(array)
             <!-- [ 5, 4, 3, 2, 1 ] -->
   <!--const reversed = array.slice().reverse();  -->

Convert [1, 2, 3] to [2, 4, 6].
 
 Solutions: 
                let array = [1,2,3]; 
                let doubled = array.map(x => x*2);
                console.log(doubled)
                <!-- [ 2, 4, 6 ]  --> 
         <!-- Returns the new Array  -->
                
   
# Summary - Core Array Methods

| Method    | Definition                                   |
| --------- | ---------------------------------------------|
| push()    | Add element to end                           |
| pop()     | Remove element from end                      |
| shift()   | Remove element from start                    |
| unshift() | Add element to start                         |
| includes()| Check if value exists (returns boolean)      |
| indexOf() | Find position of element (returns index)     |
| reverse() | Reverse array order                          |
| map()     | Transform each element (returns new array)   |
