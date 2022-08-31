- Type:: [[Book]]
- Author:: 
- Subject::
- Status:: [[In Progress]]
- Abstract::
- Summary::
    - [[CH1: Building Abstractions with Procedures]]
        - [[Computational Processes]] are the abstract things that inhabit computers. They manipulate [[data]] through the rules of a [[program]]
        - [1.1  The Elements of Programming](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1)
            - A powerful programming language is more than just a means for instructing a computer to perform tasks. The language also serves as a framework within which we organize our ideas about processes. Thus, when we describe a language, we should pay particular attention to the means that the language provides for combining simple ideas to form more complex ideas. Every powerful language has three mechanisms for accomplishing this:
                - **primitive expressions**, which represent the simplest entities the language is concerned with,
                - **means of combination**, by which compound elements are built from simpler ones, and
                - **means of abstraction**, by which compound elements can be named and manipulated as units.
            - In programming, we deal with two kinds of elements: procedures and data. (Later we will discover that they are really not so distinct.) Informally, data is `"stuff" that we want to manipulate, and procedures are descriptions of the rules for manipulating the data. Thus, any powerful programming language should be able to describe primitive data and primitive procedures and should have methods for combining and abstracting procedures and data.
            - Expressions in Scheme
                - (+ (* 3 5) (- 10 6))
Operation is always on the left, allows for nested operations without ambiguity
                - Can be deeply nested:
                    - (+ (* 3 (+ (* 2 4) (+ 3 5))) (+ (- 10 7) 6)) 
which is:
(+ (* 3
      (+ (* 2 4)
          (+ 3 5)))
     (+ (- 10 7)
      6))
                    - It gets evaluated proceduraly as follows:
                        - Evaluate the subexpression of the combination
                        - then apply the procedure of the leftmost subexpression (the operator on the left) to the arguments of the other subexpressions (the operands)
                    - For this to work, you need to know the context which it is being executed in
                    - Procedures rely on primitive cases that they fall back on
                        - Numbers equal their value
                        - operators have a procedure defined by the machine in that environment
            - [1.1.4  Compound Procedures](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1.4)
                - You can define procedures as such `(define (square x) (* x x))`
                    - in that way, you can continue nesting `(square (square 3))`
            - [1.1.5  The Substitution Model for Procedure Application](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1.5)
                - The machine understands a custom name of a procedure kind of like this:
                    - To apply a compount procedure, evaluate the body of the procedure which each formal parameter replaced by the corresponding argument
                - so given the square procedure, if we define 
`(define (fourthpow x) (square (square x)))`
                    - applicative order [*](((q-O0QEJKC))) {{[[r/moved]]}}
                        - when calling `(fourthpow 3)` the compiler looks for fourthpow in the context and (acts as though it) substitutes it with the body `(square (square x))`  then subtitutes the variable `(square (square 3))` then substitutes the innermost parenthesis with that procedures body 
`(square (* 3 3))` and evaluates it to `(square 9)`, which it expands and so on
                    - normal order[*](((Qk1st2mQL))) {{[[r/moved]]}}
                        - substituting everything until there are only primitives then reducing it to an answer
                        - when calling `(fourthpow 3)` the compiler looks for fourthpow in the context and (acts as though it) substitutes it with the body `(square (* x x))`  then subtitutes the variable `(square (* 3 3))` then substitutes the function to `(* (* 3 3 ) (* 3 3))` 
                        - once there are only primitives it evaluates it
                    - lisp uses applicative order 
            - [1.1.6  Conditional Expressions and Predicates](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1.6)
                - to do conditionals in lisp, you use the cond statement
                - ```common lisp
(define (abs x)
  (cond ((> x 0) x)
        ((= x 0) 0)
        ((< x 0) (-x))))```
                    - It evaluates the first statement then the second and so on.
                    - You can also use an else to clean this up
                        - ```common lisp
(define (abs x)
  (cond ((> x 0) (- x))
        (else x)))```
                    - Or write an if which is a special primitive that only understands two cases
                        - ```common lisp
(define (abs x)
  (if (< x 0) (- x)
      x))```
                        - `(if <__predicate__> <__consequent__> <__alternative__>)`
                - predicates must always evaluate to true or false
            - [1.1.7  Example: Square Roots by Newton's Method](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1.7)
                - Functions vs procedures[*](((1ob7O5gI4))) {{[[r/moved]]}}
                    - A function describes something (with mathematical value) while a procedure defines how to get to it. 
                    - Declarative vs Imperative knowledge
                        - What is vs How to compute
                - $$\sqrt{x} = \text{the } y \text{ such that } y \geq 0 \text{ and }  y^2 = x$$
                - Newton's method is actually procedural though
                    - whenever we have a guess __y__ for the value of the square root of a number __x__, we can perform a simple manipulation to get a better guess (one closer to the actual square root) by averaging __y__ with __x__/__y__.[21](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-10.html#footnote_Temp_33)
                        - ![](https://firebasestorage.googleapis.com/v0/b/firescript-577a2.appspot.com/o/imgs%2Fapp%2FJavier-knowledge-graph%2F1Vz7pM3b9S.png?alt=media&token=6350cb57-ec34-47a7-9654-a40b96426b53)
                        - procedurally this looks something like this:
                            - ```common lisp
(define (sqrt-iter guess x)
  (if (good-enough? guess x)
      guess
      (sqrt-iter (improve guess x)
                 x)))

(define (improve guess x)
  (average guess (/ x guess)))
(define (average x y)
  (/ (+ x y) 2))
(define (good-enough? guess x)
  (< (abs (- (square guess) x)) 0.001))
(define (sqrt x)
  (sqrt-iter 1.0 x))```
                                - 
            - [1.1.8  Procedures as Black-Box Abstractions](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.1.8)
                - `(sqrt x)` is a function defined in terms of itself
                - It also abstracts away the procedure in other pieces of data
                    - it hides the details of the implementation
                    - It however is at the whim of the names of the functions being defined correctly in the program. To tackle this, you can create a block scope (similar to **[[Closures]]** is a refrence to the place in memory that is kept 'alive' after the the function has finished running (even if it will not be called again) in JS) which allows you to define variables only for active within the definition of a function
                        - Useful if good-enough is defined differently for another operation 
        - [1.2  Procedures and the Processes They Generate](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.2)
            - Learning the rules tells you nothing about the strategy of learning to program. The rules are the basics, but you need to visualize the consequences of doing something
            - [1.2.1  Linear Recursion and Iteration](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.2.1)
        - [1.3  Formulating Abstractions with Higher-Order Procedures](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_1.3)
            - Procedures that manipulate procedures are called __higher-order procedures__.
            - given three functions that do basically the same
            - ```common lisp
(define (sum-integers a b)
  (if (> a b)
      0
      (+ a (sum-integers (+ a 1) b))))

(define (sum term a next b)
  (if (> a b)
      0
      (+ (term a)
         (sum term (next a) next b))))```
            - where term and next are functions themselves
            - You can also define a lambda (throwaway) function
    - [CH2: Building Abstractions with Data](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_chap_2)
        - An Introduction to the idea of dealing with complex data instead of complex procedures
        - [2.1  Introduction to Data Abstraction](https://mitpress.mit.edu/sites/default/files/sicp/full-text/book/book-Z-H-4.html#%_toc_%_sec_2.1)
            - So take a rational number, defined by a numerator and a denominator, this is a data structure that is defined by a pair of integers, and the operations that need to be applied to it are also defined by operations to that pair of integers. 
                - Information about the data structure is necessary to operate on it.
            - When we begin making procedures like add rational numbers, etc, the mechanics and details of the logic of these is not concerning to us. We can isolate that 
- Grokked::
