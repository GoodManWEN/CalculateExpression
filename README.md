# Calculate Expression
### A simple calculator dealing with expressions in string type ,using stack.

# Features

 - You can custom each operator's priority and behavior.
 - Expressions both with and without algebras are supported.
 
# Caution

 - spaces in input expressions will be remove while processing.
 - each expression will be converted into (expression) before processing to avoid empty stack problems.

# Installation

    $ pip install calculate_expression

#####   \* could only be installed on python3

# Usage

initialize a standard calculator:
(optional parameters "rule" & "regularization")

    from calculate_expression import ce
    standard = ce.Calculator()

You can custom your own operator sets ,default ones like this:

    # "operator":(priority,behavior)
    rule = { '+' : (0 ,lambda x,y:x+y) ,
             '-' : (0 ,lambda x,y:x-y) ,
             '*' : (1 ,lambda x,y:x*y) ,
             '/' : (1 ,lambda x,y:x/y) , 
             '^' : (2 ,lambda x,y:x**y) }

#####   \* once new operator is added ,regularization function may need to be modified commensurately.
#####   \* default regularization function: `lambda x:x.replace("**","^").replace('\\','/')`

You can check operate rules like this

    print( standard.rule )

Try a simple calculate

    print( standard.calculate('1 + 2 * 3') )

Algebra is supported

    print( standard.calculate('a + b * c' ,a = 1 ,b = 2 ,c = 3) )

Once introduced ,algebras will be stored in whose object's attribute as a dictionary
It will remain until it's updated.

    print( standard.calculate('' ,a = 1 ,b = 2 ,c = 3 ,d = 4 ,e = 1.6) ) # only update params
    print( standard.calculate('d ** 4 / e') )
    print( standard.calculate('d ** 4 / e' ,e = 0.16) )

Have fun.
