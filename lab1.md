# Lab Report 1  - Remote Acess and FileSystem

## Using the ```cd``` command

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


## Using the ```ls`` command 

1. With no arguments
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/695551f0-a840-4883-950a-107c3a2c847f)
- The working directory was `/home/lecture1`
- The output was a list of all the files in the directory`/home/lecture1`
- It was not an error

2. With a path to a directory as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/ba0f61e5-5a40-45f0-9a59-c7c38b0c561a)
- The working directory was `/home/lecture1`
- I provided the argument `messages`, so the output was a list of all the files in the directory`/home/lecture1/messages`, but without changing the working directory
- It was not an error

3. With a path to a file as an argument
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/ade99e5e-650c-4553-b50a-c15229402fc9)
- The working directory was `/home/lecture1`
- - I provided the argument `Hello.java`, so the output was a list of all the files in path `/home/lecture1/Hello.java`, which is just the file `Hello.java`
- It was not an error

