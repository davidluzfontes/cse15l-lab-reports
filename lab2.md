# Lab Report 2  - Servers and SSH Keys


##Part 1 - Chat Server

**ChatServer code**
![code](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/09ef4b8c-1576-4a34-ad64-2c33f6f5792e)

**Using /add-message**
![image](https://github.com/davidluzfontes/cse15l-lab-reports/assets/149021334/f02d662b-1b0b-40e8-a500-aad6fe8a9e79)
- The first method called was `handleRequest(URI url)`, which processes the url `url`
and handles all of the requests sent by the user
- Then, the `getPath()` method gets the path after the url, the portion after the `/`. This is used to determine if the user
went to the `/add-message` path
- Then the `getQuery()` method gets called, setting everything after the `?` to `String query`


