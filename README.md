
ASSIGNMENT 1

	 Question 
		Extend the hand-written compiler so that it can translate code 
		segments generated by the following grammar:
		
			stmt ? id := expr
				| if expr then stmt
				| while expr do stmt
				| begin opt_stmts end 
			opt_stmts ? stmt_list |?
			stmt_list  ? stmt_list; stmt | stmt

		Also, modify the grammar for handling expressions so that it can handle 
		relational operators (=, <, >) as well as arithmetic operators (+, -, *, /)
  

	Solution : grammer

	stmt ---------------> id ":=" expression
 			  									 | "if" expression "then" stmt
													 | "while" expression "do" stmt
													 | "begin" opt_stmts "end"
	opt_stmts------------> stmt_list 
													 | e
	stmt_list------------> stmt; opt_stmts
	expression-----------> expression "=" rel 
													 | rel
	rel      ------------> rel < expression2 
													 | rel > expression2 
													 | expression2
	expression2 ---------> expression2 + term 
													 | expression2 - term 
													 | term
	term ----------------> term * factor 
													 | term / factor 
													 | factor
	factor --------------> number 
													 | (expression) 
=========================================================================================													 
	
ASSIGNMENT 2(a).
	Take a language which is a subset of C. You may take any other
	language (or its subset). Define its alphabets and the tokens 
	using regular expressions. From the tokens, generate the 
	transition diagrams and display them in form of a table.
	Take a sample program in the language you have considered. 
	Perform lexical analysis for the program and generate the symbol
	table. Also, your lexical analysis module should have error 
	detection capability.

ASSIGNMENT 2(b).
	Implement a Lexical analyzer using lex for the same language
	considered above.
	
Solution:
	a) Parses the grammer_1 file and then generates the NFA for
	   each line.
	b) Combines all the NFA's and generates a single NFA.
	c) Converts the NFA to DFA
	d) Simulate the input_1 file on the DFA.
	e) Outputs the <token_class,optional attribute> for each lexeme
	   matched.
	   
=========================================================================================													 
Compilation of flex:
	flex analyser.l			
	gcc lex.yy.c -ll
=========================================================================================													 
Run of flex:
	./a.out < input_1
	./a.out < input_2
	./a.out < input_3


=========================================================================================													 
ASSIGNMENT 3(a):
	Design an LL(1) parser for the language you have used 
	in Assignment 2.The parser needs to call the lexical analyzer. 
	The Parser takes input as the source code, calls the lexical 
	analyzer to generate tokens and finally do parsing. The parser
	should also have the facility to take an arbitrary CFG and 
	generate LL(1)table and display it. Also, parsing stack should be
	displayed.Also include features like handling ambiguity, 
	elimination of left recursion etc. !!!!

ASSIGNMENT 3(b):
	Implement a Parser using Yacc for the language used in 
	Assignment 1 (b).
=========================================================================================													 
ASSIGNMENT 4: Simple 3 address code generation
	Output of Parser:
           x:=y op z
  where x,y and z are "id", and �op� stands for any operator.
 
  The three address code is
 
      t1:=y*z
      t2:=x+t1
      d:=t2
 
  where t1 and t2 are compiler-generated temporary variables.
=========================================================================================													 
