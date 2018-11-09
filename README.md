# THIS DOCUMENT IS UNDER CONSTRUCTION

The best practices which are not be able to checked by automatic tools.

Scope: general programming and javascript.

# Naming
Choose the names carefully. If you can't name well, you probably can't manage your code.
* Choose descriptive name. Examples:

*Bad*: var d; // elapsed time in days
*Good*: var elapsedTimeInDays;

TODO add more examples
* Keep the name short if possible. However, don’t be afraid of long name if it is necessary to describe object. Normally, the larger scope the name is the longer length it is.
* Use Pronounceable and correct English names
* Use Searchable Names. Single-letter names and numeric constants have a particular problem in that they are not easy to locate across a body of text.
* Methods should have verb or verb phrase
* Classes and objects should have noun or noun phrase
* Boolean variable name should have `is` prefix. Sometimes `can`, `should`, or `has` can be used when appropriate. E.g. isVisible, shouldUpdate, canAbort, hasEntity.
* Keep the name up to date with the implementation
* ....

# Duplication
* Avoid copy and paste code
* Avoid copy, paste and modify code
* Avoid different code but the same logics
* Avoid different variables keep the same information (to try keep single source of truth).
# Error handling
* NEVER catch error and keep silent.
* Each exception that you throw should provide enough context to determine the source and location of an error
* Create informative error messages and pass them along with your exceptions. Mention the operation that failed and the type of failure.

TODO give examples

# Performance
## N+1 problems
## Be careful with premature optimization
...
# Comments
* You should first strive to make your code as simple as possible to understand. Then at the point where the code cannot be made easier to understand should you begin to add comments. For example:
* Explain “why” you must write the code in a certain way, what the rationale for choosing this or that method is, etc.
* Explain how the code works when your write complex algorithm.
* Keep the comments up to date.
* Avoid redundant comments. A comment is redundant if it describes something that adequately describes itself. For example:

i++; // increment i
* Remove Commented-Out Code. We don’t need to keep the old code by commenting-out, the source control does this. And most of the time, commented-out code is useless.
* At the top of the definition of a function, a short description should be provided, explaining what the function is aiming to do, what are the parameters. Especially, in most of scripting languages, it is important to indidate the type of the input paramenters.   
# Function design
* Keep the function small and does one thing well
* The number of arguments should smaller than 3.
* A function should have NO side effects
# Complexity
## Keep technical code away from business code
# Others
### Commit messages
