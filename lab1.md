# Lab Report 1  - Remote Acess and FileSystem

## Using the `cd` command

1. With no arguments
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/0c4a86ab-642b-4323-8377-326e9b31a9f9)
- The working directory was `/home/lecture1/messages`
- The output was supposed to change to the directory in the argument, but since I gave no arguments, it changed it to `/home`
- It was not an error


2. With a path to a directory as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/da5498f9-b998-48d5-b2e9-3104dd0e41a8)
- The working directory was `/home`
- The output was supposed to change to the directory in the argument, so it changed it to `/home/lecture1`
- It was not an error


3. With a path to a file as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/0573cd80-f159-4bce-a391-f6e201ba48f9)
- The working directory was `/home/lecture1`
- The output was supposed to change to the directory in the argument, but since the argument provided was not a directory, it returned an error.
- The output is an error because the argument provided was a file instead of a directory



## Using the `ls` command 

1. With no arguments
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/695551f0-a840-4883-950a-107c3a2c847f)
- The working directory was `/home/lecture1`
- The output was a list of everything in the directory`/home/lecture1`
- It was not an error


2. With a path to a directory as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/2fd25009-d342-45a8-b58b-3df98d6de87a)
- The working directory was `/home/lecture1`
- I provided the argument `messages`, so the output was a list of everything in the directory`/home/lecture1/messages`, but without changing the working directory
- It was not an error


3. With a path to a file as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/ade99e5e-650c-4553-b50a-c15229402fc9)
- The working directory was `/home/lecture1`
- I provided the argument `Hello.java`, so the output was a list of everything in the path `/home/lecture1/Hello.java`, which is just the file `Hello.java`
- It was not an error


## Using the `cat` command 

1. With no arguments
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/76d5251f-530d-4361-bda1-8a3807666579)
- The working directory was `/home/lecture1`
- The output was taking user input and printing it out. This happens until the user closes it using `^C`
- It was not an error


2. With a path to a directory as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/af015823-4be9-4fe2-b8df-141210c85347)
- The working directory was `/home/lecture1`
- I provided the argument `messages`, which is a directory, so the output was an error message
- It was an error message, because `cat` was expecting a file as an argument, but I provided a directory


3. With a path to a file as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/ea6df5e9-3663-46f9-b32d-1b479940415a)
- The working directory was `/home/lecture1`
- I provided the argument `Hello.java`, so the output was printing out the contents of the file onto the terminal.
- It was not an error
