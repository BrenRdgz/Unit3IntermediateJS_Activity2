# Unit3IntermediateJS_Activity2

    - ¿What is a closure? 
    It is when a function is able to remember and access the parent function's variables even when that function us executing outside its lexical scope.

    - Give me an example of closure. 
    function makeCounter(){
      let count = 0;
      return function increase(){
        count = count+1;
        return count;
      };
    }
    const count1 = makeCounter();
    console.log(count1());

    - What is ()() in code? 
    It allows to execute the function inside the parent function
    EX: 
    const a = 'Hey! ';
    function firstWord(){
      const b = "What's ";

      function  restOfStatement(){
          const c = 'up?'
          return a + b + c;
      }
      return restOfStatement;
    } 
    console.log(firstWord()); //returns the function restOfStatement
    console.log(firstWord ()()); // return the result when the function restOfStatement is executed 

    
    
    - Move the variable after the closure (the function inside the function) and explain what happens. 
    the function is executed successful because even though the function is declared before the variable, the funciton is executed after so,
      the program knows the variable's value.
      
    const a = 'Hey! ';
    function firstWord(){
        function  restOfStatement(){
          const c = 'up?'
          return a + b + c;
        }
        const b = "What's ";
        return restOfStatement;
     } 
    const greeting = firstWord();
    console.log(greeting());

    - Change var for let and explain why the logic is not affected 
    It's still working because the function local is called after the variable's assignment.
    const a = 'Hey! ';
    function firstWord(){
        function  restOfStatement(){
          const c = 'up?'
          return a + b + c;
         }
        let b = "What's ";
        return restOfStatement;
    } 
    const greeting = firstWord();
    console.log(greeting());

    - Scope chain, an example of it, how many closures can we nest 
    we can nest many closures as many as we want
    
    const a = 'Hey! ';
    function firstWord(){
      const b = "What's ";
      function  restOfStatement(){
        const c = 'up? '
        function setName(d){
            console.log(a+b+c+d)
        }
        return setName;
      }
    return restOfStatement;
    } 
    firstWord()()('Brenda');
    
    - They are conflicts between the closure and the global scope? 
    There are'nt conflict because they are different scopes.
    const a = 'Hey! ';
    var d = 'Otro nombre';
    function firstWord(){
      const b = "What's ";
      function  restOfStatement(){
        const c = 'up? '
        function setName(d){
            console.log(a+b+c+d)
        }
       return setName;
      }
    return restOfStatement;
    } 
    firstWord()()('Brenda');
    
    - Advantages of closures. 
      - Data hiding
      - Encapsulation
      - Function Factory 
      

    - ¿What is data hiding and encapsulation? 
    It is when a variable cannot be accessed by a external function and this variable doen't exist outside the function  when the variables is declared.

    - Give me an example of privacy with closures.
    function makeCounter(){
      let count =0;
      return function increment(){
        count = count +1;
        return count
      }
    }
    const count1 = makeCounter();
    count1();
    count1();
    console.log(count1());
    console.log(count1.count); //this output is undifined because we canot access to variable count
    

    - What happens if you create two counters with the same closure? 
    each counter is independent because each counter creates its lexical scope. 
    
    function counter(){
      let counter = 0;
      function incrementCounter(){
        counter++;
        console.log(counter);
        }
      return incrementCounter;
     }
     const counter1 = counter();
     const counter2 = counter();
      counter1();
      counter1();
      counter2();
      counter2();

    - How can we add more functions as a decrement counter? Give an example of it. 
    function makeCounter(){
      let count = 0;
      return{
        increment : function(){
            count = count+1;
            return count;
        },
        decrement:function(){
            count = count -1;
            return count;
        },
        getValue:function(){
            return count;
        }
      }
    }
    const count1 = makeCounter();
    console.log(count1.increment());
    console.log(count1.increment());
    console.log(count1.increment());
    console.log(count1.getValue());
    console.log(count1.decrement());
    console.log(count1.getValue());
      
      
    - What are the disadvantages of closures? 
    overconsumption of memory
