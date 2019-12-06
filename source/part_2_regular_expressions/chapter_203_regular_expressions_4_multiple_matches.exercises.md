{EXERCISE BEGIN 01}
Match all the occurrences of exactly three digits in the file examples.txt
{EXERCISE SOLUTION 01}
``` sh
$ grep -E "[0-9]{3}" examples.txt 
Police 101
007
Cyborg 009
```
{EXERCISE END 01}

{EXERCISE BEGIN 02}
The log file simple.log contains the status of HTTP responses, which is a three digit number preceded TODO and followed by a space. HTTP statuses are categorised according to the initial digit and 4xx responses (that is 400, 401, 402, and so on) are considered TODO resource errors. Count how many HTTP 4xx responses are in the file for each type of error.
{EXERCISE SOLUTION 02}
``` sh
$ grep -Eo " 4[0-9]{2} " simple.log | sort | uniq -c
      2  403 
    213  404 
      2  416 
      1  481
```
{EXERCISE END 02}

{EXERCISE BEGIN 03}
The log file simple.log contains the IP address of the client for each request. IP addresses are made of four numbers separated by dots (i.e. `A.B.C.D`), where each number goes from 0 to 255 (thus having from 1 to 3 digits). Find the 5 IP addresses that occur the highest number of times in the file, counting them
{EXERCISE SOLUTION 03}
``` sh
$ grep -Eo "[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}" simple.log | sort | uniq -c | sort -nr | head -n 5
    482 66.249.73.135
    364 46.105.14.53
    357 130.237.218.86
    273 75.97.9.59
    113 50.16.19.13
```

The regular expressions is made of four repetitions of `[0-9]{1,3}`, which matches 1 to 3 adjacent digits, separated by `\.` which is a literal dot (remember that a dot without the escape backslash matches any character). The following `sort` and `uniq -c` provide the counting, the last `sort -nr` orders the list again using the numerical sort (which orders according to the count, as this is at the beginning of each line), and in reverse order, starting from bigger numbers down to 1. The last `head -n5` at last selects the top 5 from the list.
{EXERCISE END 03}

{EXERCISE BEGIN 04}
The file simple.log contains the HTTP method used in the request (for example `GET` or `POST`) followed by a space and the rest of the log line. For each request that uses a `GET` print the HTTP method and everything that follows.
{EXERCISE SOLUTION 04}
``` sh
$ grep -Eo "GET .*" simple.log 
```

The pattern `.*` is one of the most common ones in regular expressions. As `.` matches any character and `*` matches 0 or more repetitions of the previous component, `.*` means any repetition of any character, or "anything" for TODO short. This is extremely useful whenever there are long dishomogeneous TOOD parts of a line that you want to match without writing a (probably very complex and long) regular expressions that matches them.
{EXERCISE END 04}
