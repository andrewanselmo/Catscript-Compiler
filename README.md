NOTE: Due to university policy, I cannot publish source code but can share upon request.

# DESCRIPTION 

For my senior capstone at MSU I developed a compiler for the low level programming language CatScript. For each of the rules found in the CatScript grammar below we were tasked with implementing methods to tokenize, parse, evaluate, and then compile. We were provided wiith a web interface to interact directly with the CatScript compiler so you can see each of the processes in real time. 

Above you will find my capstone potfolio where I discuss my personal CatScript documentation, design patterns, UML diagrams, and design trade offs for the project. 

# OUTCOMES 

- Learned how code becomes executable instructions through tokenization, parsing, evaluation, and compilation.
- Learned how to formally define a programming language with grammar.
- Enhanced testing abilites through writing Java unit tests for a classmates compiler.
- Learned how to write documentation for a programming language.
- Learned to create UML diagrams.

# VIDEO DEMO 
https://youtu.be/MdFMTVmyl3E


### CatScript Grammar

```ebnf
catscript_program = { program_statement };

program_statement = statement |
                    function_declaration;

statement = for_statement |
            if_statement |
            print_statement |
            variable_statement |
            assignment_statement |
            function_call_statement;

for_statement = 'for', '(', IDENTIFIER, 'in', expression ')', 
                '{', { statement }, '}';

if_statement = 'if', '(', expression, ')', '{', 
                    { statement }, 
               '}' [ 'else', ( if_statement | '{', { statement }, '}' ) ];

print_statement = 'print', '(', expression, ')'

variable_statement = 'var', IDENTIFIER, 
     [':', type_expression, ] '=', expression;

function_call_statement = function_call;

assignment_statement = IDENTIFIER, '=', expression;

function_declaration = 'function', IDENTIFIER, '(', parameter_list, ')' + 
                       [ ':' + type_expression ], '{',  { function_body_statement },  '}';

function_body_statement = statement |
                          return_statement;

parameter_list = [ parameter, {',' parameter } ];

parameter = IDENTIFIER [ , ':', type_expression ];

return_statement = 'return' [, expression];

expression = equality_expression;

equality_expression = comparison_expression { ("!=" | "==") comparison_expression };

comparison_expression = additive_expression { (">" | ">=" | "<" | "<=" ) additive_expression };

additive_expression = factor_expression { ("+" | "-" ) factor_expression };

factor_expression = unary_expression { ("/" | "*" ) unary_expression };

unary_expression = ( "not" | "-" ) unary_expression | primary_expression;

primary_expression = IDENTIFIER | STRING | INTEGER | "true" | "false" | "null"| 
                     list_literal | function_call | "(", expression, ")"

list_literal = '[', expression,  { ',', expression } ']'; 

function_call = IDENTIFIER, '(', argument_list , ')'

argument_list = [ expression , { ',' , expression } ]

type_expression = 'int' | 'string' | 'bool' | 'object' | 'list' [, '<' , type_expression, '>']

```
