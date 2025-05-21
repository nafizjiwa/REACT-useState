# REACT-useState 

### useState Hook

    - manages state for functional components.</br>
    - The set method is asynchronous and doesn't update changes immediately</br>
    - To update the state call set method, React then batches updates to optimize performance.</br>
Techniques to resolve the asynchronous issue </br>

#### 1. Functional Updates: When the new state depends on the previouse state, Pass a function as an argument to setState ensures you get the latest state value
   
        const Counter = () => {
              const [count, setCount] = useState(0);
      
          const incrementCount = () => {  setCount(prevCount => prevCount + 1);    };
          return ( <div>
                        <p>Count: {count}</p>
                        <button onClick={incrementCount}>  Increment   </button>
                  </div>         );
      };
#### 2. useEffect Hook: 
   - Allows side effects to be performed in functional components.
   - How? Monitors state change so code can be run in response to that state change
   - Action? Logging, Fetching data, or updating the DOM based on the new state


          import React, { useState, useEffect } from 'react';
          const Counter = () => {
              const [count, setCount] = useState(0);
          
              useEffect(() => { console.log("Count updated:", count); }, [count]);
                       ***** HERE: useEffect logs the new count value whenever [count] changes ******
          
              const incrementCount = () => { setCount(count + 1); };
          
              return (
                  <div>
                      <p>Count: {count}</p>
                      <button onClick={incrementCount}> Increment </button>
                  </div>  );
          };
          export default Counter;

   
#### 3. Triggering Updates Correctly: Pass the correct value to the update function.
   - handleClick function directly calls setCount with count + 1.
   - 
         const handleClick = () => { setCount(count + 1); };
            return (
                   <button onClick={handleClick}>  Increment  </button>
### EXAMPLE REACT APPLICATION COUNTER
- ##### //App.js

         import React from 'react';
         import HookCounter from './components/hookCounter';
         function App() {
            return (
                    <div>
                      <h1>React Counter Example</h1>
                      <HookCounter />
                    </div>
                  );    
            }
        export default App;

- ##### //components/Counter.js

          import React, { useState } from 'react';
            
            function HookCounter() {
              const initialCount = 0;
              const [count, setCount] = useState(initialCount);
            
              const increment = () => {
                setCount(prevCount => prevCount + 1);
              };
            
              const decrement = () => {
                setCount(prevCount => prevCount - 1);
              };
            
              const reset = () => {
                setCount(initialCount);
              };
            
              return (
                <div>
                  <h1>Count: {count}</h1>
                  <button onClick={increment}>Increment</button>
                  <button onClick={decrement}>Decrement</button>
                  <button onClick={reset}>Reset</button>
                </div>
              );
            }
            
            export default HookCounter;
