# REPORT
## Make Command
Why do we need make?

When we make a small program we simply compile and execute but in case of large files we are mainly focussed on compilation and not debugging, make makes it easy to compile and we need not to focus much on compilation.

If one program is compiled and it takes 10 minutes then we need not to compile every program again and again (to waste 10 mins. again) because it will compile only the file that is changed so it is better than a shell script.


Makefile have a definite structure that we have to follow.
Structure

Target : Dependencies

<tab> commands
Purpose
Problem with ordinary compiling

Error Prone: there are lot of compilation flags used during the compilation and manually we have to write flags and we can mistype.

Distraction from the debugging process

Time consuming: we have rebuild the code again

Inefficient on larger projects
Make

Suppose we have large number of sourcefiles.c

We convert them to object files sourcefile1.o sourcefile2.o sourcefile3.o

Then create the executable file.

Unlike script if we change one source file, only its object file is made and compiled and not all source files are compiled.

Explain all the flags and commands written in the presentations.

-I: Add the directory dir to the list of directories to be searched for header files. Directories named by -I are searched before the standard system include directories. If the directory dir is a standard system include directory, the option is ignored to ensure that the default search order for system directories and the special treatment of system headers are not defeated .

Note: If -I. Is present the compiler will search header files in a current file.

-Wall: gcc -Wall enables all compiler’s warning messages. This option should always be used, in order to generate better code.

For demo: http://www.rapidtables.com/code/linux/gcc/gcc-wall.htm

-pedantic-errors: Issue all the mandatory diagnostics, and make all mandatory diagnostics into errors. This includes mandatory diagnostics that GCC issues without -pedantic but treats as warnings.

-save-temps: So when we compile the program main.c with -save-temps flag we get the main.i and main.s intermediate files in the current directory (along with the print executable). The preprocessed output is stored in the temporary file that has the extension .i.

-std=c99: Assume that the input sources are for c99 standard.

Targets: What should be the output.

Make <target_name>

Make all

If we omit “all” it will run the all one.

Commands:

Actions that should be run to get the result.

Dependencies:

Things that are needed.

Comments:

Denoted by hashtag (#).

Variables:

We define at the top. E.g. which compiler to be used like gcc

###

###
Demo

all (the one used in make all)

Hellomake (executable)

_____________

/ \

Hellomake.o hellofunc.o

/ \ / \

Hm.c hm.h hf.c hm.h

CC=gcc # compiler to use

CFLAGS=-I. #need during compilation

# dot(.) for current directory

#special targets

.PHONY: clean

# this will not create any new files.

PHONY should be consistent even if we need to create new targets similar to clean. If we

don’t write the above target, then it can collide with a “clean” if present. Any variable that doesn’t have any dependency we have to declare with PHONY.

What’s the meaning of the word “PHONY”?

To run a makefile with specific name:

make -f makefile_simple

Auto variables

Target: dependencies

gcc -o $@

# $@ will replace with the target

$^ will list all dependencies

$< first dep

%.o: %.c

Will take all the objects.

We have to take special care for dependencies. What can we do to automate the list of deps.

Qmake or cmake?

Can we have makefile for HTML (web dev)?

If we use:

pdflatex file.tex

10 times

Then it will run for 10 times even there is no change.
