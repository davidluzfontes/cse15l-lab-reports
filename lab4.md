# Lab Report 4 - Vim

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/2fd1bdb8-38e5-4a6d-94bc-9d20521ba766)
Keys pressed: `<up> <enter>`. 

I pressed `<up>` so I could find the `ssh dsaldanhadaluzfontes@ieng6.ucsd.edu` command in my bash history, and pressed `<enter>` to run it. Due to my ssh key, this command instantly logged me in to my ieng6 account

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/818f2533-f64a-466e-8ecf-29ebc4d9a842)
Keys pressed: `c s 1 5 l <tab> <enter>`.

I typed `c s 1 5 l` to start going into my workspace for this course, then, pressed `<tab` to autocomplete the rest, and `<enter>` to run the command. This put me into `/home/linux/ieng6/cs15lwi24/dsaldanhadaluzfontes`, where I can execute the rest of the tasks

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/c0eb8dd7-7471-470e-809a-4b6fb3bc1095)
Keys pressed: `g i t <space> c l o n e <space> <ctrl>+v <enter>`. 

I typed the `git clone ` command because I want to clone a git repository. Then, I pressed `<ctrl>+v` to paste the ssh URL of my private fork into the terminal, and `<enter>` to run it. Due to my GitHub ssh key, I was able to clone the private repository into my working directory.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/44383559-9496-46c6-8652-fbb0b43f196e)
Keys pressed: `c d <space> <shift>+c <tab> <enter>`. 

I typed the `cd ` command because I want to change directory, then `<shift>+c` to type `C`, the first character of the name of the directory I cloned the repository into, and `<tab> <enter>` to autocomplete and run, as it was the only directory in my working directory whose name started with `C`.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/c7cf0a4a-d2a1-4c13-85ba-93651dcc70c1)
Keys pressed: `l s <enter>`. 

I ran the `ls` command to list the files in the working directory, so I could remember the names of the files I needed to use.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f83eec00-7618-41b1-a820-de93e2ed2d93)
Keys pressed: `b a s h <space> t <tab> <enter>`. 

I typed the `bash ` command because I want to run a `.sh` file. Then I typed `t <tab>` because t is the first letter of the name of the `test.sh` file i want to run, and nothing else in the current directory has a name starting in t. Then I pressed `<enter>`, which ran the `javac -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar *.java` and `java -cp .:lib/hamcrest-core-1.3.jar:lib/junit-4.13.2.jar org.junit.runner.JUnitCore ListExamplesTests` commands in the `test.sh` file.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/d652c0e5-0b68-4f5a-ab03-33b49ae62323)
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/6de0adfb-a64f-4acf-89f3-0efc1a29b47a)
Keys pressed: `v i m <space> <shift>+l <tab> . <tab> <enter>`. 

I ran the `vim ` command because I want to use vim to edit a file. Then, I pressed `<shift>+l <tab>`, which autocompleted to `ListExamples` because both of the files in this directory whose name starts with `L` continues with `istExamples`. Then I typed `.` to differentiate the file I wanted, `ListExamples.java` from the `ListExamplesTests.java` file, so that pressing `<tab>` would autocomplete. Pressing `<enter>` opened the file in vim.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f459d239-3be5-4947-afd2-62a4b4914e10)
Keys pressed: `4 3 j e`. 

I pressed `4 3 j` because, from the test results, I knew the error was caused by line 44, so o could go 43 lines downwards, from line 1 to 44. I then found the error and pressed `e` to go to the last character of the word.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/63577fd8-2285-4009-b414-df3dee34e317)
Keys pressed: `x i 2 <esc>`. 

I pressed `x` to remove the character after the cursor, 1, then `i` to go into insert mode. From there I typed `2` to correct the error, and `<esc>` to quit insert mode

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/26f2d259-e3cc-4082-8186-8a01cba54f67)
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/56be10e2-6e9e-45ea-bef4-5c894dbebfd9)
Keys pressed: `: w q <enter>`.

I pressed the `:` key to input a command, then `wq`, `w` to write(save) my edits, and `q` to quit. I then pressed `<enter>` to run that command and exit vim.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/5b6283e5-e372-4f66-9c9c-2e3c7a3f5767)
Keys pressed: `<up> <up> <enter> `.

I pressed `<up> <up>` so I could find the `bash test.sh` command, which was 2nd in my bash history, and pressed `<enter>` to run it. This command reran the commands `test.sh` file, using the fixed `ListExamples.java` file.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f3694ea6-e6eb-439d-9b61-2704a39c5711)
Keys pressed: `g i t <space> c o m m i t <space> - a <space> - m <space> " f i x " <enter>`.

I used the `git commit ` command to commit all of the changes I made to the git branch I am working on. I added the `-a` flag to add my changes to the list of changes to commit, equivalent to using `git add .` and the `-m` file to add a message to the commit, `fix`. Then I pressed `<enter>` to run it.

<br>

![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/8783ff28-2830-4f19-88dd-bafb8c975873)
Keys pressed: `g i t <space> p u s h<enter>`

I used the `git push` command to push all of my changes to my private GitHub fork. Then I pressed `<enter>` to run it.




