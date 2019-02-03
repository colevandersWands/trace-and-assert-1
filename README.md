learning objectives
* gaining confidence in mental tracing
* guessing intermediate values
* hypothesis-driven code tracing & studying


you can complete these exercises directly from your fork by inspecting this page and copy-pasting the snippets into devtools console. fill in your solutions by editing this page, writing in the actual values for each challenge

for each piece of code you will be given several inputs to study, ie.
> a:3, b:4    -->   1:?, 2:?, 3:?  

each entry on the right hand side of the arrow represents an assertion point in the snippet.  the exercise here is to correctly fill in each of the blanks.



### The Challenges
* [variables](#variables)  
    * value swap
    * block scope 'let'
    * block scope 'var'
* [reference types](#reference-types)  
    * comparing reference types
    * reference vs value
    * no-copy array
    * yes-copy array
    * dots vs brackets
* [conditionals](#conditionals)  
    * ||, if/else, truthyness
    * if, else if, else
    * nested conditionals
* [iteration](#iteration)
    * accumulating
    * repeating until
    * once per thing
    * breaking down

---
---

## Variables 

**Value Swap**    

[on pytut](https://goo.gl/27fPqs)  
[interactive example](https://github.com/elewa-academy/value-swap)  

the code:
```js
{
  const expected = ;                

  let a = ;                        
  let b = ;                       
  let temp = ;                   
   
  temp = b;                       console.assert( === temp, '1: temp');
  b = a;                          console.assert( === b, '2: b');
  a = temp;                       console.assert( === a, '3: a');

  const actual = temp;            
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:1, b:2, temp:3            -->   1:?, 2:?, 3:?
a:'a', b:'b', temp:'temp'   -->   1:?, 2:?, 3:?
a:true, b:false, temp:null  -->   1:?, 2:?, 3:?
a:'', b:0, temp:undefined   -->   1:?, 2:?, 3:?
```
your notes:

---

**Block Scope 'let'**

[on pytut](https://goo.gl/Ym63eU)  
[interactive example](https://github.com/elewa-academy/nesting-blocks-let)  

the code:
```js
{
  const expected = ;              

  let a = ;                       
  let b = ;  
  let c = ;                       

  {
    let a = b;                  console.assert( === a, '1: a');
    {
       a = c;                   console.assert( === a, '2: a');                     
    }
    a = a;                      console.assert( === a, '3: a');
  }

  const actual = a;               
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:1, b:2, c:3         -->   1:?, 2:?, 3:?
a:'', b:0, c:false    -->   1:?, 2:?, 3:?
a:true, b:false, c:9  -->   1:?, 2:?, 3:?
```
your notes:  

---

**Block Scope 'var'**  

[on pytut](https://goo.gl/GRjDLQ)  
[hoisting](https://github.com/elewa-academy/hoisting) 
[hoisting & blocks](https://github.com/elewa-academy/hoisting-and-blocks)
[let vs var](https://github.com/elewa-academy/block-scope-let-vs-var)  


the code:
(refresh the page each time before running this exercise)  
```js
{
  const expected = ;              
                       
  let b = ;  
  let c = ;                       

  {
    var a = b;                    console.assert( === a, '1: a');
    {
       let a = c;                 console.assert( === a, '2: a');
    }                        
                                  console.assert( === a, '3: a');
  }
                                  console.assert( === a, '4: a');

  const actual = a;              
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
b:2, c:3         -->   1:?, 2:?, 3:?, 4:?
b:0, c:false     -->   1:?, 2:?, 3:?, 4:?
b:false, c:9     -->   1:?, 2:?, 3:?, 4:?
```
your notes:  

---
---

## Reference Types


**comparing reference types**  

[on pytut](https://goo.gl/8wNY4c)  
[more about this](https://github.com/elewa-academy/reference-vs-value)

the code:
```js
{
  const expected = ;                           
  
  const a = [1];
  const b = [2, 1];
  const c = [1, 2];
  
  const b_0 = b.shift();          console.assert( === b[0], '1: b[0]');
                                  console.assert( === (a[0] === b[0]), '2: a[0] === b[0]');
  const a_eq_b = a === b;         console.assert( === a_eq_b, '3: a_eq_b');
  const a_same_vals_b = JSON.stringify(a) === JSON.stringify(b);
                                  console.assert( === a_same_vals_b, '4: a_same_vals_b');
  
  const c_1 = c.pop();            console.assert( === c[0], '5: c[0]');
                                  console.assert( === (a[0] === c[0]), '6: a[0] === c[0]');
  const a_eq_c = a === c;         console.assert( === a_eq_c, '7: a_eq_c');
  const a_same_vals_c = JSON.stringify(a) === JSON.stringify(c);
                                  console.assert( === a_same_vals_c, '8: a_same_vals_c');
  
  const b_eq_c = b === c;         console.assert( === b_eq_c, '9: b_eq_c');
                                  console.assert( === (b[0] === b[0]), '10: b[0] === c[0]');
  const b_same_vals_c = JSON.stringify(b) === JSON.stringify(c);
                                  console.assert( === b_same_vals_c, '11: b_same_vals_c');

  const d = [b_0, c_1];           console.assert( === d[0], '12: d[0]');
                                  console.assert( === d[1], '13: d[1]');
  a.push(b_0);                    console.assert( === a[0], '14: a[0]');
                                  console.assert( === a[1], '15: a[1]');
  const a_eq_d = a === d;         console.assert( === a_eq_d, '16: a_eq_d');
  const a_same_vals_d = JSON.stringify(a) === JSON.stringify(d);
                                  console.assert( === a_same_vals_d, '17: a_same_vals_d');
  

  const actual = a_same_vals_b && a_same_vals_c && a_same_vals_d && b_same_vals_c;              
 
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
(no inputs)  ->  1:?, 2:?, 3:?, 4:?, 5:?, 6:?, 7:?, 8:?, 9:?, 10:?, 11:?, 12:?, 13:?, 14:?, 15:?, 16:?, 17:? 
```
your notes:  

---

**Reference vs. Value**  

[on pytut](https://goo.gl/Rhktpu)  
[more about this](https://github.com/elewa-academy/reference-vs-value)

the code:
```js
{
  const expected = ;                           
  
  let val_1 = ;
  let ref_1 = [];

  let val_2 = val_1;            console.assert( === (val_1 === val_2), '1: val_1 === val_2');
  let ref_2 = ref_1;            console.assert( === (ref_1 === ref_2), '2: ref_1 === ref_2');

  val_2++;                      console.assert( === val_2, '3: val_2');
                                console.assert( === (val_1 === val_2), '4: val_1 === val_2');
  
  ref_2.push(value_2);          console.assert( === ref_2[0], '5: ref_2[0]');
                                console.assert( === ref_1[0], '6: ref_1[0]');

  ref_1 = null;                 console.assert( === ref_2[0], '7: ref_2[0]');
  ref_2 = null;                 console.assert( === (ref_1 === ref_2), '8: ref_1 === ref_2');

  const actual = val_1;              
 
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
val_1:''      -->   1:?, 2:?, 3:?, 4:?, 5:?, 6:?, 7:?, 8:?
val_1:1       -->   1:?, 2:?, 3:?, 4:?, 5:?, 6:?, 7:?, 8:?
```
your notes:  

---

**no-copy arrays**  

[on pytut](https://goo.gl/xX64Cg)  
[more about this](https://github.com/elewa-academy/reference-vs-value)

the code:
```js
{
  const expected = ;           
                       
  const a = [];                  
  const b = [];                  
  const x = ;
  const y = ;                   
  
  a.push(b);                     console.assert( === a[0], '1: a[0]');
  b.push(x);                     console.assert( === b[0], '2: b[0]');
  a.push(b);                     console.assert( === a[0], '3: a[0]');
  b.push(y);                     console.assert( === b[1], '4: b[1]');
  a.push(b);                     console.assert( === a[1], '5: a[1]');

  const actual = a;              
  
  const assert_act = JSON.stringify(actual);
  const assert_exp = JSON.stringify(expected);
  console.assert(assert_act === assert_exp, 'actual !== expected');
}
```
the values:
```js
x:2, y:3         -->   1:?, 2:?, 3:?, 4:?, 5:?
x:'x', y:'y'     -->   1:?, 2:?, 3:?, 4:?, 5:?
x:null, y:0      -->   1:?, 2:?, 3:?, 4:?, 5:?
x:{}, y:[]       -->   1:?, 2:?, 3:?, 4:?, 5:?
```
your notes:  

---


**yes-copy arrays**  

[on pytut](https://goo.gl/UCT8Co)  
[more about this](https://github.com/elewa-academy/reference-vs-value)

the code:
```js
{
  const expected = ;        
                       
  const a = [];                     
  const b = [];                      
  const x = ;
  const y = ;               
  
  a.push(b.slice());          console.assert( === a[0], '1: a[0]');
  b.push(x);                  console.assert( === b[0], '2: b[0]');
  a.push(b.slice());          console.assert( === a[0], '3: a[0]');
  b.push(y);                  console.assert( === b[1], '4: b[1]');
  a.push(b.slice());          console.assert( === a[1], '5: a[1]');

  const actual = a;         
  
  const assert_act = JSON.stringify(actual);
  const assert_exp = JSON.stringify(expected);
  console.assert(assert_act === assert_exp, 'actual !== expected');
}
```
the values:
```js
x:2, y:3         -->   1:?, 2:?, 3:?, 4:?, 5:?
x:'x', y:'y'     -->   1:?, 2:?, 3:?, 4:?, 5:?
x:null, y:0      -->   1:?, 2:?, 3:?, 4:?, 5:?
x:{}, y:[]       -->   1:?, 2:?, 3:?, 4:?, 5:?
```
your notes:  

---

**Dots vs Brackets**  

[on pytut](https://goo.gl/2G6nuu)  
[extra resource](https://github.com/elewa-academy/variables-and-types/tree/master/dots-vs-brackets) 

the code:
```js
{
  const expected = [];          

  const arr = [];
  const obj = {a: 1, b: 2};
  const a = ;
  const b = ;                   

  arr.push(obj.a);            console.assert( === arr[0], '1: arr[0]');
  arr.push(obj.b);            console.assert( === arr[1], '2: arr[1]');

  arr.push(obj[a]);           console.assert( === arr[2], '3: arr[2]');
  arr.push(obj[b]);           console.assert( === arr[3], '4: arr[3]');

  const actual = arr;           
  
  const assert_act = JSON.stringify(actual);
  const assert_exp = JSON.stringify(expected);
  console.assert(assert_act === assert_exp, 'actual !== expected');
}
```
the values:
```js
a:'a', b:'b'      -->   1:?, 2:?, 3:?, 4:?
a:'b', b:'a'      -->   1:?, 2:?, 3:?, 4:?
a:1, b:2          -->   1:?, 2:?, 3:?, 4:?
a:2, b:1          -->   1:?, 2:?, 3:?, 4:?
```
your notes:  

---
---


## Conditionals

conditional statements add a new level of complextiy to tracing your code, not ever line will be executed.  The challeges below will have an assertion for each line of executable code even that line is not reached.  Fill in those asserts with the values that _would_ be logged if that line of code were executed.

**||, if/else, truthyness**  

[on pytut](https://goo.gl/TgqxaR)

the code:
```js
{
  const expected = ;     
                       
  const a = ;                     
  const b = ;
  let x = null;
  let y = null;               
  
  let condition = a || b;     console.assert( === condition, '1: condition');
  if (condition) {            console.assert( === !!condition, '2: truthyness');
    x = b;                    console.assert( === x, '3: x'); 
    y = a || b;               console.assert( === y, '4: y'); 
  } else {                    console.assert( === !!condition, '2: truthyness');
    x = a;                    console.assert( === x, '3: x'); 
    y = a || b;               console.assert( === y, '4: y'); 
  };
  
  const actual = y;
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:true, b:false      -->   1:?, 2:?, 3:?, 4:?
a:false, b:true      -->   1:?, 2:?, 3:?, 4:?
a:0, b:1             -->   1:?, 2:?, 3:?, 4:?
a:1, b:0             -->   1:?, 2:?, 3:?, 4:?
a:null, b:false      -->   1:?, 2:?, 3:?, 4:?
a:false, b:null      -->   1:?, 2:?, 3:?, 4:?
a:'', b:' '          -->   1:?, 2:?, 3:?, 4:?
a:' ', b:''          -->   1:?, 2:?, 3:?, 4:?
a:2, b:3             -->   1:?, 2:?, 3:?, 4:?
a:3, b:2             -->   1:?, 2:?, 3:?, 4:?
```
your notes:  

---


**if, else if, else**  

[on pytut](https://goo.gl/zhTS2m)

the code:
```js
{
  const expected = ;               
                     
  const a = ;
  const b = ;
  const c = ;
  const result = null;             
  
  const cond_1 = b && a;          console.assert( === cond_1, '1: cond_1');
                                  console.assert( === !!cond_1, '2: cond_1 truthyness');
  const cond_2 = a || c;          console.assert( === cond_2, '3: cond_2');
                                  console.assert( === !!cond_2, '4: cond_2 truthyness');
  if (cond_1) {               
    result = cond_1;              console.assert( === result, '5: if result');
  } else if (cond_2) {
    result = cond_2;              console.assert( === result, '5: else if result');
  } else {
    result = cond_1 + cond_2;     console.assert( === result, '5: else result');
  };

  const actual = result;
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:true, b:'', c:1      -->  1:?, 2:?, 3:?, 4:?, 5:?
a:false, b:'', c:0     -->  1:?, 2:?, 3:?, 4:?, 5:?
a:true, b:'', c:0      -->  1:?, 2:?, 3:?, 4:?, 5:?
a:false, b:'', c:1     -->  1:?, 2:?, 3:?, 4:?, 5:?
a:false, b:' ', c:1    -->  1:?, 2:?, 3:?, 4:?, 5:?
a:true, b:' ', c:1     -->  1:?, 2:?, 3:?, 4:?, 5:?
```
your notes:  

---



**nested conditionals**  

[on pytut](https://goo.gl/D9R3HS)

the code:
```js
{
  const expected = ;             
                     
  const a = ;
  const b = ;
  const result = null;           
  
  if (a) {
    if (b) {                      console.assert( === a && b, '1: a && b');
      result = 'w: ' + a + b;     console.assert( === result, '2: if if result');
    } else {                      console.assert( === a && !b, '1: a && !b');
      result = 'x: ' + a + b;     console.assert( === result, '2: if else result');
    };
  } else {
    if (b) {                      console.assert( === !a && b, '1: !a && b');
      result = 'y: ' + a + b;     console.assert( === result, '2: else if result');
    } else {                      console.assert( === !a && !b, '1: !a && !b');
      result = 'z: ' + a + b;     console.assert( === result, '2: else else result');
    };
  };

  const actual = result;
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:0, b:0    -->  1:?, 2:?
a:0, b:1    -->  1:?, 2:?
a:1, b:0    -->  1:?, 2:?
a:1, b:1    -->  1:?, 2:?
```
your notes:  

---
---


## Iteration

tracing execution becomes even more complicated with iteration, the same lines of code are now being executed multiple times but with different values.  this means you can no longer simply put hard-coded assertions on each line.  
instead you will have to build a log of the loop's behavior and compare it to a hard-coded prediction.  We've provided one completed example for each challenge so you can get the idea how this works.

**accumulating**  

[on pytut](https://goo.gl/YFn6Zd)

the code:
```js
{
  const expected = ;            
             
  const things = ;
  let result = null;            
             
  let i = 0;                     const iterlog = [];
  while (i < things.length) {    const iteration = {};
    result += things[i];         iteration.res = result;
    ++i;                         iteration.i = i;
                                 iterlog.push(iteration);
  };
  
  { // assert loop behavior
     const hypotheses = [ ? ];         
     const were_correct = JSON.stringify(hypotheses) === JSON.stringify(iterlog);
     console.assert(were_correct, {hypotheses, iterlog})
  }

  const actual = result;
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
things:[-1, 0, 1]            --> [ {res:-1, i:1}, {res:-1, i:2}, {res:0,i:3} ]
things:[-3, -2, -1]          --> [ ? ]
things:[true, false, 1, 0]   --> [ ? ]
things:['words', 5, 1e3]     --> [ ? ]
things:[]                    --> [ ? ]
```
your notes:  

---

**repeating until**  

[on pytut](https://goo.gl/jbvs2o)

the code:
```js
{
  const expected = ;           
                     
  let a = ;
  let b = ;
  const c = ;
  let steps = 0;               
                        const iterlog = [];
  while (a !== b) {     const iteration = {};
    a -= c;             iteration.a = a;       
    b += c;             iteration.b = b;       
    steps++;            iteration.steps = steps;
                        iterlog.push(iteration);
  };
  
  { // assert loop behavior
     const hypotheses = [ ? ];         
     const were_correct = JSON.stringify(hypotheses) === JSON.stringify(iterlog);
     console.assert(were_correct, {hypotheses, iterlog})
  }

  const actual = steps;
  
  console.assert(actual === expected, 'actual !== expected');
}
```
the values:
```js
a:10, b:0, c:1      --> [ ? ]
a:8, b:2, c:1       --> [ ? ]
a:7, b:5, c:1       --> [ {a:6,b:6,steps:1} ]
a:13, b:1, c:3      --> [ ? ]
a:0, b:-28, c:7     --> [ ? ]
a:15, b:-9, c:3     --> [ ? ]
```
your notes:  

---

**once per thing**  

[on pytut](https://goo.gl/Gbtsu9)

the code:
```js
{
  const expected = ;                  
                     
  const things = ;
  const result = [];                 
  
  let i = 0;                         const iterlog = []; 
  while (i < things.length) {        const iteration = {};
    const new_thing = !things[i];    iteration.new = new_thing;
    result.push(new_thing);          iteration.res = result.slice(); 
    i += 1;                          iteration.i = i;
                                     iterlog.push(iteration);
  };
  
  { // assert loop behavior
     const hypotheses = [ ? ];         
     const were_correct = JSON.stringify(hypotheses) === JSON.stringify(iterlog);
     console.assert(were_correct, {hypotheses, iterlog})
  }
  
  const actual = result;

  const assert_act = JSON.stringify(actual);
  const assert_exp = JSON.stringify(expected);
  console.assert(assert_act === assert_exp, 'actual !== expected');
}
```
the values:
```js
things:[false,true]     --> [ {new:true, res:[true], i:1}, {new:false, res:[true,false], i:2} ] 
things:[0,1]            --> [ ? ]
things:['',' ']         --> [ ? ]
things:[Infinity,NaN]   --> [ ? ]
things:[[],{}]          --> [ ? ]
things:[[1],{1}]        --> [ ? ]
```
your notes:  

---

**breaking down**  

[on pytut](https://goo.gl/iupw2c)

the code:
```js
{
  const expected = ;               
                     
  const word = ;
  const letters = [];              

  let i = 0;                      const iterlog = []; 
  while (i < word.length) {       const iteration = {};
    const letter = word[i];       iteration.letter = letter;
    letters.push(letter);         iteration.letters = letters.slice();
    i = i + 1;                    iteration.i = i;
                                  iterlog.push(iteration);
  };
  
  { // assert loop behavior
     const hypotheses = [ ? ];         
     const were_correct = JSON.stringify(hypotheses) === JSON.stringify(iterlog);
     console.assert(were_correct, {hypotheses, iterlog})
  }

  const actual = letters;
 
  const assert_act = JSON.stringify(actual);
  const assert_exp = JSON.stringify(expected);
  console.assert(assert_act === assert_exp, 'actual !== expected');
}
```
the values:
```js
word:"word"       --> [ ? ]
word:""           --> []
word:"\n\t"       --> [ ? ]
word:"\e\\"       --> [ ? ]
word:"3.5"        --> [ ? ]
```
your notes:  

---

_the end_

___
___
### <a href="http://janke-learning.org" target="_blank"><img src="https://user-images.githubusercontent.com/18554853/50098409-22575780-021c-11e9-99e1-962787adaded.png" width="40" height="40"></img> Janke Learning</a>
