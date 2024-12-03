# Java Script

### Smarter Debugging Alternatives with console
 - ```console.dir()``` for Inspecting Objects
   Instead of using console.log() to print out objects, which can be hard to read, try console.dir(). It displays an interactive list of the properties of a specified object, making it easier to explore deeply nested structures.
   ```js
   const user = { name: 'Alice', age: 25, preferences: { theme: 'dark', notifications: true } };
   console.dir(user, { depth: null });
   ```
 - ```console.clear()``` to Keep the Console Clean
   If you’re logging frequently during development, your console can get cluttered quickly. Instead of manually clearing it or sifting through endless logs, use console.clear() to clear the console when you no longer need old logs.
   ```js
   console.clear();
   ```
 - ```console.group()``` and ```console.groupEnd()``` for Organizing Logs
   Sometimes you need to organize related logs into groups for better readability. console.group() allows you to group multiple logs together, and you can even nest groups for hierarchical data. Use console.groupEnd() to close the group.
   ```js
   console.group('User Info');
   console.log('Name: Alice');
   console.log('Age: 25');
   console.group('Preferences');
   console.log('Theme: Dark');
   console.log('Notifications: Enabled');
   console.groupEnd(); // Closes 'Preferences'
   console.groupEnd(); // Closes 'User Info'
   ```
- ```console.table()``` for Displaying Tabular Data
  If you’re dealing with arrays of objects or large datasets, console.table() can format your output into a nice, readable table, making it easier to visualize complex data.
  ```js
  const users = [
  { name: 'Alice', age: 25 },
  { name: 'Bob', age: 30 },
  { name: 'Charlie', age: 35 }
  ];
  console.table(users);
  ```
- ```console.time()``` and ```console.timeEnd()``` for Measuring Performance.
   Need to know how long a function takes to run? Use console.time() at the start of the function and console.timeEnd() at the end to measure the execution time of a block of code. This is especially useful for performance optimization.
   ```js
   console.time('fetchData');
   // Simulate some async operation
   setTimeout(() => {
      console.timeEnd('fetchData');
   }, 2000);
   ```

