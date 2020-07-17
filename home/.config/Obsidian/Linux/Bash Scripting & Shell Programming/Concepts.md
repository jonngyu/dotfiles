
# #!
Called the **shebang**, this will denote what interpreter is used for the script.

		#! path/to/interpreter
	
These are some script interpreters:

		#! /bin/bash
		#! /bin/csh
		#! /bin/ksh
		#! /bin/zsh

If the script doesn't have a shebang, the commands in the script will execute based on the default ***$SHELL***. Better to be explicit and specify the interpreter to be used due to: 
* different features 
* different syntax

# Variables
- Storage locations that have a name
- Name-value pairs
-  syntax : VARIABLE_NAME="Value"
-  Variables are case sensitive
-  By convention variables are uppercase
-  to use a variable, have it preceded by a $ or ${}
-  the use of ${} is for when the variable is preceded or followed by additional information
-  example
		
		#! /bin/bash
		MY_SHELL="bash"
		echo "I am ${MY_SHELL}ing on my keyboard"
		
		> I am bashing on my keyboard
	 
- Can also assign command output to a variable
- example
		
		#! /bin/bash
		SERVER_NAME=$(hostname)
		echo "You are running this script on ${SERVER_NAME}."
		
		> You are running this script on linuxsvr
# Tests
- Syntax: 
- "[ condition-to-test-for ]"
- example:
- [ -e /etc/passwd ]
	- this test checks if /etc/passwrd exists 
	- if it does, it returns TRUE or exits with 0
	- if it doesn't, it returns FALSE or exits with 1
- check help test or man test (Bash only)
- tests can also be used for arithmetic operators

# Making Decisions - The IF statement
		 if [condition-is-true]
		then
			command 1
			command 2
			command n
		fi
 
Example Script
	
		#! /bin/bash
		MY_SHELL="bash"

		if [ "$MY_SHELL" = "bash" ] 
		then
			echo "You seem to like the bash shell."
		fi

if/else

		if [ condition-is-true ]
		then
			command N
		else
			command N
		fi
		
Example script

		#! /bin/bash
		MY_SHELL="csh"

		if [ "$MY_SHELL" = "bash" ] 
		then
			echo "You seem to like the bash shell."
		else
			echo "You don't seem to like the bash shell."
		fi

if/elif/else

		if [ condition-is-true ]
		then
			command N
		elif [ condition-is-true ]
		then
			command N
		else
			command N
		fi
		
Example script

		#! /bin/bash
		MY_SHELL="csh"

		if [ "$MY_SHELL" = "bash" ] 
		then
			echo "You seem to like the bash shell."
		elif [ "$MY_SHELL" = "csh" ]
		then
			echo "You seem to like the csh shell."
		else
			echo "You don't seem to like the bash or csh shells."
		fi
# For Loop
To perform an action or series of actions on multiple items, use a for loop.

	for VARIABLE_NAME in ITEM_1 ITEM_2 ITEM_N
	do
		command 1
		command 2
		command N
	done

Example Script
	
	#! /bin/bash
	for COLOR in red green blue
	do
		echo "COLOR": $COLOR"
	done

	> COLOR: red
	> COLOR: green
	> COLOR: blue
How this works: red is assigned to the variable COLOR, which then the code block is executed. This happens again for green and blue. The code block stops after blue since there are no more items in the list.

Lists can be created with " "

	MAMMALS="man bear pig dog cat sheep"

Example Script

	#! /bin/bash
	COLORS="red green blue"
	for COLOR in $COLORS
	do
		echo "COLOR": $COLOR"
	done
It is common to store the list into a variable.



# Accepting User Input (STDIN)
The read command accepts STDIN (standard input). Usually from a keyboard.
Syntax:

		read -p "PROMPT" VARIABLE

Example:

		read -p "Enter a user name: " USER
# Exit Statuses / Return Code
 