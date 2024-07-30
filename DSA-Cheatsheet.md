# Data structures and Algorithms

### Data Structure

 - Data structure is the arranging,processing, retrieving, and storing the data in a computer memory with well defined way by the experts based on the need.

![image](https://github.com/user-attachments/assets/2b82b1b3-0fa1-473a-87b1-f15fe1bb0af8)


### Linear Data Structure
 - where the data is arranged sequentially, each element attached with they perivious and next element.
 - **Ex**. Array, Stack, Queue, Linked List, etc.
 
 #### Static Data Structure
 - Static Data structure have fixed memoery size, easier to access the element.
 - **EX**. Array
     - **Array**

          ![image](https://github.com/user-attachments/assets/cf998776-6e9a-47e7-b155-7eedd1b673ed)


        ```
        # Python
         
         my_array = [10, 20, 30, 40, 50]
         
         # Accessing elements
         print(my_array[0])  # Output: 10
         print(my_array[2])  # Output: 30

         ```
         ```
         # Modifying elements
         my_array[1] = 25
         print(my_array)  # Output: [10, 25, 30, 40, 50]

         ```
         ``` 
         # Length of the array
         print(len(my_array))  # Output: 5
         ```
         ```
         # Iterating through elements
         for element in my_array:
             print(element)
         ```

         ```
         # Slicing (creating subarrays)
         subarray = my_array[1:4]
         print(subarray)  # Output: [25, 30, 40]
         ```
         ```
         # Adding elements
         my_array.append(60)  # Add to the end
         print(my_array)  # Output: [10, 25, 30, 40, 50, 60]
         ```

         ```
         my_array.insert(2, 35)  # Insert at index 2
         print(my_array)  # Output: [10, 25, 35, 30, 40, 50, 60]
         ```

        ```
         # Removing elements
         my_array.remove(30)  # Remove the first occurrence of 30
         print(my_array)  # Output: [10, 25, 35, 40, 50, 60]
         ```
        ```
         del my_array[0]  # Delete element at index 0
         print(my_array)  # Output: [25, 35, 40, 50, 60]
         ```
        ```
         # Searching for elements

         ## It will return Bool value Ture | False
         if 40 in my_array:
             print("40 found")

         # if the element not found mean it will lead to a ValueError
         my_list = [10, 20, 30, 40, 50]
         index = my_list.index(30)
         print(index)  # Output: 2

         # Returns the possition of the element
         my_list = [10, 20, 30, 40, 30]
         count = my_list.count(30)
         print(count)  # Output: 2
         ```
         ```
         # Concatenating arrays
         another_array = [70, 80]
         combined_array = my_array + another_array
         print(combined_array)  # Output: [25, 35, 40, 50, 60, 70, 80]
         ```
         ```
         # sort() --> Modifies the original list in-place,
         # Returns None, use a stable sorting algorithm (Timsort)
         my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
         my_list.sort()
         print(my_list)  # Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]

         my_list.sort(reverse=True) # Reverse the element in the array
         ```
         ```
         # sorted() Creates a new sorted list, Leaves the original list unchanged,
         # use a stable sorting algorithm (Timsort)
         my_list = [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]
         sorted_list = sorted(my_list)
         print(sorted_list)  # Output: [1, 1, 2, 3, 3, 4, 5, 5, 5, 6, 9]   

         print(my_list)  # Output: [3, 1, 4, 1, 5, 9, 2, 6, 5, 3, 5]

         students = [('Alice', 95), ('Bob', 88), ('Charlie', 92)]
         sorted_students = sorted(students, key=lambda x: x[1])  # Sort by score
         ```
         ```
         # Traversing is access the all the element in the array to do some options.

         # Using the for loop
         my_list = [10, 20, 30, 40, 50]
         for element in my_list:
             print(element)

         #Using the range()
         my_list = [10, 20, 30, 40, 50]
         for i in range(len(my_list)):
             print(my_list[i])

         # enumerate() 
         my_list = [10, 20, 30, 40, 50]
         for index, value in enumerate(my_list):
             print(index, value)

         # List Comprehension
         my_list = [10, 20, 30, 40, 50]
         squared_list = [x**2 for x in my_list]
         print(squared_list)  # Output: [100, 400, 900, 1600, 2500]

         ```
       
 #### Dynamic Data Structure
 - In the dynamic data structure the size is not fixed, It can be randomly updated during the runtime.
 - **EX**. queue, stack, Linked list, etc

   
