Interview questions from https://www.toptal.com/javascript/interview-questions

1. The value of 'bar' is also an object if the value is null.  In that case, a boolean should be used to ensure only values not equal to null are shown.

2. When using 'strict mode' both a and b would be undefined.  Without 'strict mode', var a = b = 3 would translate to b=3 and var a = b.  Therefore, b would be a global variable whil a would not.    

3. 'this' in the inner function doesn't have access to the object 'this' and therefore will return undefined.

Outter funcs evaluate to:
this.foo = bar;
self.foo = bar;

Inner func evaluate to:
this.foo = undefined;
self.foo = bar;

4.  This protects from outside variables affecting the source code.  The closure around file prevents naming conflicts.

5. 'use strict' will throw more errors that otherwise would be ignored.  If errors are thrown, this can help with debugging.  

6. The first will return {bar: 'hello'}.  The second will return undefined.  That is because javascript with automatically insert semicolons if none are seen at the end of a statement.  Therefore, the second function would be 'return;' which would return undefined.

7.  If the second line was '===' instead it would be true.  However, '==' uses loose equality.  The answer coiuld vary due to floating point precision.

8.  The order is 1, 4, 3, 2.  Console.logs are siimple operations that execute immediately.  setTimeouts get executed next.  The one with a 1000 ms delay gets executed last.

9. function isPalindrome(str){
    str.toLowerCase();
    str2 = str.split('').reverse.join('');
    return str === str2 ? true : false;
}

10. function sum(x,y){
    if(!y){
        return x + y;
    }else{
        return function(y){
            return x + y;
        });
    }

}

11. a) 5 gets logged to the console.  i is defined with var which gives it global scope.

b) Using let instead of var would give a specific block scope to that iteration.  The result would then be 4.

12. This sets to keys with the values of each array element that are set to undefined.

13. array 1: length=5 lasts=j,o,n,e,s
array 2: length=5 last=j,o,n,e,s

Array 2 references array 1.  That's why the logs appear the same.

14. a) '122'.  The 1 is converted to a string because javascript sees the 2nd item is a string.
b) '32'.  Here 2 is converted to a number and then added.  3 is converted to a string with the 2nd addition operation.
c) '02'.  The 2nd 1 is converted to a number which sums to 0.  Then 0 is converted to a string.
d) '112'.  The first one if converted to a number, but then converted back after the 2nd + operator is seen.
e) 'NaN2'.  '-' can't be used with strings. Then NaN is converted to a string because a + operator is seen with a string.  
f) NaN.  This is because you cannot do addtion with NaN. 

15. Adding a setTimeout will pass the action off to the browser so that the call stack will handle the recursion instead.

16. A closure is allows inner functions to remember variables from outer functions after the outer function is executed.  It is used to incapsulate logic and keep variables private.  

Ex.:
function guessingGame() {
    let hasWon = false;
    let randNum = Math.floor(Math.random()*100);
    let guessCount = 0;

    return function guessNum(guessedNum){
        if(hasWon){
            return 'The game is over, you already won!';
        }

        guessCount ++;
    
        if(randNum === guessedNum){
            hasWon = true;
            let message = `You win! You found ${randNum} in ${guessCount} guesses.`;
            return message;
        }
        if(guessedNum > randNum){
            return `${guessedNum} is too high!`;
        }
        if(guessedNum < randNum){
            return `${guessedNum} is too low!`;
        };
    
    };
}

17. The expressions are converted to boolean values and then evaluated by the || and && operators.  If one of the || values is false, the first true value is returned.  If both of the && values are true, the 2nd value is returned.  Therefore:
0 || 1 = 1
1 || 2 = 1
0 && 1 = 0
1 && 2 = 2

18. The === checks for strict equality and therefore returns false.  The == is loose equality.  The string gets converted to false and therefore the first expression returns true.

19. Javascript automatically stringifies the parameter value.  a[b] and a[c] are both the same.  456 was the last property set and therefore a[b] =456.

20. This is a recursive function call.  It will be called until n=1.  The result is 10!.

21. x will be 1.  The inner function is able to access the outter function's parameters.  

22.  The code outputs undefined and John Doe.  You can fix this error by binding hero like this hero.getSecretIdentity.bind(hero);

23.  function Traverse          (p_element,   p_callback) {
   p_callback(p_element);
   var list = p_element.children;
   for (var i = 0; i < list.length; i++) {
       Traverse(list[i],p_callback);  // recursive call
   }
}

24. The first this.length call references 10.  The scope of the the second call is the arguments array which has a length of 2.

25. The var statements get hoisted to the top of the function scope its inside of.  But the parameter in the catch block is only visible inside itself.  It will print 1, undefined, 2.

26. The result is undefined.  Witihn the function, x is present, but not assigned a value.

27. i is assigned only to each block of the for loop execution.  Therefore, the output is 0, 1, 2,3,4.

28. The first statement is true, but the 2nd is false.  It is false because the first comparison is true which equates to one.  Then 1>1 is false.

29. Use array.push to add to the end and array.unshift to add to the beginning.

30.  a) It will create empty spots and assign 99 to the 10th spot.
b) a[6] will return undefined because of the empty space.

31. This will output true because they NULL is treated as an undefined variable.  It should be null instead if the keyword is to be used.

32. It will be 'string'.  'number' is returned first, which is a type of string.

33. It will be 5, 5, 5, 5, 5.  That's because var is scoped to the complete for loop.  Therefore, the settimeouts execute at the end of the loop when i = 5.

34. NaN represents itself, not a number.  You can test it by using Number.isNaN().

35. Output = 3.  That is because b is not declared within the inner function until b=3.  Then the number is logged.  

36. Use (typeof x === 'number') && (x % 1 === 0). Or use Number.isInteger();

37. var obj = {a: 1 ,b: 2}
var objclone = Object.assign({},obj);

This only works though because there are no nested elements.  Otherwise, the nested elements would reference the same piece of memory.