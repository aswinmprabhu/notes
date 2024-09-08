Bash tricks  
  
Stdout to file  
** $ls > out.txt**  
  
Stderr to file   
**$ ls 2> out.txt**  
  
Both stdout and stderr to a file  
** $ls &> out.txt**  
  
Chaining commands  
**$ cat test | sort | grep x**  
  
Use file as input  
** $sort < input.txt**  
  
Clear a file  
**$ :> out.txt**  
  
Ignore output  
** $ls > /dev/null**  
  
Run command in the background   
**nohup firefox https://freecodecamp.org &**  
  
Create files from file1.txt to file100.txt  
**c9::$ touch file{1..100}.txt**  
  
Create app.html, app.css and app.js  
** $touch app.{html,css,js**}  
  
Chain commands  
**$ mkdir test && touch ./test/test.txt**  
  
Append to a file  
** $ls >> out.txt**  
  
See bash history  
**$ history**  
  
Bulk operate on files with for loop  
** $for f in ./*.gz; do tar zxvf "$f"; done**


---
