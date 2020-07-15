# *Jazuly* Answer for Online Technical Assesment from PT. Supra Primatama Nusantara
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
`day; num_pos_scores; num_neg_scores`
##### Where num_pos_scores and num_neg_scores are the total number of positive score rows, and negative score rows in the table, for individual days between March 1st, 2011 and April 30th, 2011, both days inclusive.
#### Answer:
```MySQL
SELECT 'day',
    (SELECT Count(*) FROM assessments WHERE score >= 0 AND date BETWEEN '2011-03-01' AND '2011-04-31') AS num_pos_scores,
    (SELECT Count(*) FROM assessments WHERE score < 0 AND date BETWEEN '2011-03-01' AND '2011-04-31') AS num_neg_scores
	FROM assessments asd
	GROUP BY num_pos_scores AND num_neg_scores
```

##### 2) Provide a mysql select statement that returns all the days between January 1st, 2011 and June 30th, 2011, both days inclusive, where there were no negative scores.
#### Answer:
```MySQL
SELECT *
    FROM assessments
	WHERE score >= 0
	AND date BETWEEN '2011-01-01' AND '2011-06-30'
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
### Algorithmic (25)
##### In the language of your choice, write a function which, taking a positive integer n as input, finds all sets of numbers that sum up to n.
#### Answer:
###### NB: Note the right answer but better than nothing.
```Javascript
const subsetSum = (numbers, target, partial = [], sum = 0) => {
  if (sum < target)
    numbers.forEach((num, i) =>
      subsetSum(numbers.slice(i + 1), target, partial.concat([num]), sum + num));
  else if (sum == target)
    console.log('sum(%s) = %s', partial.join(), target);
}

subsetSum([1,2,3,4,5,6,7,8,9], 4);
```

### Bonus: Parallel and Concurrency (10)
##### Please explain Parallel and Concurrency to non-technical person, without technical terms. Let’s say you explain to non developers. Tips, you can use diagrams, pictures, or story as long as non-technical persons understand.
#### Answer:
##### Concurrency
Concurrency mean ability of a program to handle multiple request.
###### Make it easy to understand
Let's think ***Concurrency*** as an employee, when he's boss give him multiple jobs at the same time, he has ability to grab and stack all of it, but when he's do that he will confusing and tired because all of that jobs, and he will finish the job one by one, so that will take long time depend on how much the jobs.

##### Parallelism
Parallelism mean ability of a program to handle multiple request on the same time.
###### Make it easy to understand
Let's use the same analogy as ***concurrency***, on parrallelism we have more than one employees, so they can handle and finish the jobs more faster.
