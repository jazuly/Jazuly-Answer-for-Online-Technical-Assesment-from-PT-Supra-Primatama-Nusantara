# biznetAnswerJazuly
### Shell (10)
##### 1) Create a single line script that returns the number of httpd processes that are running on the current machine?
#### Answer:
```shell
ps -eo comm,etime,user | grep apache2
```

##### 2) From the current folder (/tmp), provide some bash commands that will rename all the *.txt files in mig33/inner_folder/ to *.dat?
#### Answer:
```shell
for file in /tmp/mig33/inner.folder/*.txt; do mv "$file" "${file%.txt}.dat"; done
```

### SQL (15)
##### 1) Provide a mysql select statement to return the following resultset structure:
#### Answer:
```MySQL
SELECT 'day',
    (SELECT Count(*) FROM assessments WHERE score >= 0 AND date between '2011-03-01' and '2011-04-31') as num_pos_scores,
    (SELECT Count(*) FROM assessments WHERE score < 0 AND date between '2011-03-01' and '2011-04-31') as num_neg_scores
FROM assessments asd
GROUP BY num_pos_scores AND num_neg_scores
```

### NodeJS, Python, Golang, or PHP (20)
##### 1) Write a function which, taking in a positive integer n as input, returns an array of all primes lower than n.
#### Answer:
```php
function isPrime($n) { 
    if ($n <= 1) 
        return false; 
  
    for ($i = 2; $i < $n; $i++) 
        if ($n % $i == 0) 
            return false; 
  
    return true; 
} 
  
function printPrime($n) {
    if ($n < 0) {
	echo 'Only accepted Positif Value';
	return false;
    }

    for ($i = 2; $i <= $n; $i++)  
    { 
        if (isPrime($i)) 
            echo $i . " "; 
    } 
}

printPrime(5);
```

### JavaScript (30)
##### We have a data service returning json data from another server (Server to Server), you get json-encoded as:
```javascript
[{"username":"ali","hair_color":"brown","height":1.2},{"username":"marc","hair_color":"blue","height":1.4},{"username":"joe","hair_color":"brown","height":1.7},{"username":"zehua","hair_color":"black","height":1.8}]
```

##### In an effort to reduce transfer size, we want to transfer the data in the following json format instead:
```javascript
{"h":["username","hair_color","height"],"d":[["ali","brown",1.2],["marc","blue",1.4],["joe","brown",1.7],["zehua","black",1.8]]}
```

#### Answer:
```javascript
let jsn = '[{"username":"ali","hair_color":"brown","height":1.2}, {"username":"marc","hair_color":"blue","height":1.4},{"username":"joe","hair_color":"brown","height":1.7},{"username":"zehua","hair_color":"black","height":1.8}]';
let obj = JSON.parse(jsn);
let rst = { h: null, d: [] };

obj.forEach((value) => {
  if (!rst.h) rst.h = Object.keys(value);
  rst.d.push(Object.values(value))
})
```
