# biznetAnswerJazuly
# Shell (10)
### 1) Create a single line script that returns the number of httpd processes that are running on the current machine?
## Answer:
ps -eo comm,etime,user | grep apache2

### 2) From the current folder (/tmp), provide some bash commands that will rename all the *.txt files in mig33/inner_folder/ to *.dat?
## Answer:
for file in /tmp/mig33/inner.folder/*.txt; do mv "$file" "${file%.txt}.dat"; done

# SQL (15)

# NodeJS, Python, Golang, or PHP (20)
### 1) Write a function which, taking in a positive integer n as input, returns an array of all primes lower than n.
## Answer:
function isPrime($n) 
{ 
    if ($n <= 1) 
        return false; 
  
    for ($i = 2; $i < $n; $i++) 
        if ($n % $i == 0) 
            return false; 
  
    return true; 
} 
  
function printPrime($n) 
{ 
    for ($i = 2; $i <= $n; $i++)  
    { 
        if (isPrime($i)) 
            echo $i . " "; 
    } 
}

printPrime(10);

# JavaScript (30)
### We have a data service returning json data from another server (Server to Server), you get json-encoded as:
[{"username":"ali","hair_color":"brown","height":1.2},{"username":"marc","hair_color":"blue","height":1.4},{"username":"joe","hair_color":"brown","height":1.7},{"username":"zehua","hair_color":"black","height":1.8}]
### In an effort to reduce transfer size, we want to transfer the data in the following json format instead:
{"h":["username","hair_color","height"],"d":[["ali","brown",1.2],["marc","blue",1.4],["joe","brown",1.7],["zehua","black",1.8]]}
## Answer:
let jsn = '[{"username":"ali","hair_color":"brown","height":1.2}, {"username":"marc","hair_color":"blue","height":1.4},{"username":"joe","hair_color":"brown","height":1.7},{"username":"zehua","hair_color":"black","height":1.8}]';
let obj = JSON.parse(jsn);
let key = null;
let val = [];

obj.forEach((value) => {
  if (!key) key = Object.keys(value);
  val.push(Object.values(value))
})

let rst = { h: key, d: val };
