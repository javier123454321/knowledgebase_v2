- Type:: [[Book]]
- Source:: 
- Author:: 
- Subject::
- Status:: [[In Progress]] 
- Abstract::
    - An encyclopedia like overview of the things that developers learn in Computer Science education. Being self taught is great and probably the norm, however, just because some concepts don't appear often in the majority of your work, doesn't mean that you should not learn them. This is an overview of those concepts about the theory, foundations, and history of computation that is often not optimized for when your learning resources focus solely on employability. 
- Summary::
    - Data Structures
        - [[Hash Table]]
            - Combines [[Linked List]] and [[Arrays]]
            - Computes an integer by hashing the content to an index
                - This can cause collisions which have to be accounted for can make it not the best any more. You can store an array in a given key or create a link to another [[Hash Table]]
            - This index is the bucket which it will be retrieved from.
        - [[Tree]]
            - Similar to a [[Linked List]]
            - Has one node which is the head but each node can have multiple children
            - Every child has only one parent
        - [[Binary Tree]]
            - Each node has 0, 1, or 2 children
    - Compilation
        - The process of parsing a language and compiling it to code that machines understand. C# compiles to an intermediate language that can then be compiled at execution time, which is better for portability. 
        - Lexical Analisys 
            - Takes words and transforms them to tokens - pieces of information that the compiler understands. 
                - (variable, x), (operator, ==), (number, "10")... (token lexene)
        - Parsing
            - After tokenizing the words, the parser assigns meaning to them. It is assigning value to the random bits of data in the program in smaller bits.
            - if then
        - Semantic analysis
            - What is the meaning of the program, and do we have the information to carry it out? This is the step that binds decisions of how the language 'works'. Semantic analysis defines things like hoisting, lexical scoping, etc.
        - Optimization 
            - reduce code from human readable to machine readable. No need to keep variable names like user_is_signed_in or whatever. 
        -  Code Gen
            - Turn the instructions into machine readable code. Dynamic languages compile on the fly and don't execute unless the line is currently being analyzed. 
- Grokked::
