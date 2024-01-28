# Lab Report 2  - Servers and SSH Keys


## Part 1 - Chat Server

**ChatServer code**
![code](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/0e25060c-9298-49d2-b92a-2d3ccc2937c7)


**Using /add-message**
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f02d662b-1b0b-40e8-a500-aad6fe8a9e79)
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/c5884390-bb6c-4b77-975e-68736f710cac)
- The usage of /add-message in both screenshots call the same methods: `handleRequest(URI url`, `getPath()`,`getQuery`, and `split(String regex)`.

- The first method called was `handleRequest(URI url)`, which processes the url `url`
and handles all of the requests sent by the user.
- Then, the `getPath()` method gets the path after the url, the portion after the `/`. This is used to determine if the user
went to the `/add-message` path.
- Then the `getQuery()` method gets called, setting everything after the `?` to `String query`.
- The `split(String regex)` method is called several times splitting `query` into the parts we want to use.
first, it is split at the `&` to separate the user from the message, then, split at the `=` to get the message content `message`
and the name of the user `user`.
    - In the first screenshot, `s=Hello&user=Me` gets split so that `user` is `Me` and `message` is `Hello`
    - In the second screenshot, `s=Hi&user=Wife` gets split so that `user` is `Wife` and `message` is `Hi`
- Finally, `user` and `message`, together with `": "` and `"\n"` are concatenated onto the end of `String messageHistory`, 
which is a field part of the `Handler` class that stores the message history. `messageHistory` then gets returned and displays.
    - In the first screenshot, `messageHistory` starts as `""` and ends as `"Me: Hello\n"`
    - In the second screnshot, `messageHistory` starts as `"Me: Hello\n"` and ends as `"Me: Hello\nWife: Hi\n"`

## Part 2 - SSH

Path to the private key on my computer                                              
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/0259918b-34a9-4755-a86b-5ba8a411dcae)

Path to public key on ieng6
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/25a21984-3964-4619-9d71-f3fe9ebcbbe0)

Login without using my password
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/6ab82e46-c753-444a-b849-1f841ace23f8)

## Part 3 - Conclusion
Something I learned from the lab during week 2 is the number of reserved ports. 
When following the lab document, I was told to run my server on port `6041`, `6000` for lab room B260 + `41` for the number of my computer. After failing to open my server, I asked a tutor for help, and he told me that port was probably reserved. Upon further research, we found that all of the ports from `6000` to `6063`, which everyone in the room would have to use, were reserved. 
The server loaded correctly after I tried another port number.
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/4645d073-5a1c-4dd3-8e04-44edac0edc96)


