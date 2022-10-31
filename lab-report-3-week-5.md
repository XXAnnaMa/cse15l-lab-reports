CSE15L - Week 3 Lab Report
Name: Xiaoxiang(Anna) Ma
Date: 10/30/2022

**command `find`**

* find `-name`

1. example 1:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -name "chapter-1.txt"
./technical/911report/chapter-1.txt
```
This command is used to search for the existence of the file "chapter-1.txt" in the directory "technical". It is useful because this command can help us find the target file in an unknown and huge resource library (the string inside the quotation marks must be the same as the case of the target file name).


2. example 2:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -name "bill.txt"
./technical/government/Env_Prot_Agen/bill.txt
```
This command is used to search for the existence of the file "bill.txt" in the directory "technical". It is useful because this command can help us find the target file in an unknown and huge resource library (the string inside the quotation marks must be the same as the case of the target file name).


3. example 3:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -name "1471-213X-1-1.txt"
./technical/biomed/1471-213X-1-1.txt
```
This command is used to search for the existence of the file "1471-213X-1-1.txt" in the directory "technical". It is useful because this command can help us find the target file in an unknown and huge resource library (the string inside the quotation marks must be the same as the case of the target file name).

---
* find `-regex`

1. example 1:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -regex ".*chapter-1.txt"
./technical/911report/chapter-1.txt
```
This directive is used to search for files (different from -name) matching the path ".*chapter-1.txt" in the current directory "technical". It is useful because this command searches for files by path, so it is more precise than just searching for filenames (avoids the case of overlapping filenames).

2. example 2:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -regex ".*bill.txt"
./technical/government/Env_Prot_Agen/bill.txt
```
This directive is used to search for files matching the path ".*bill.txt" in the current directory "technical". It is useful because this command searches for files by path, so it is more precise than just searching for filenames (avoids the case of overlapping filenames).

3. example 3:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -regex ".*1471-213X-1-1.txt"
./technical/biomed/1471-213X-1-1.txt
```
This directive is used to search for files matching the path ".*1471-213X-1-1.txt" in the current directory "technical". It is useful because this command searches for files by path, so it is more precise than just searching for filenames (avoids the case of overlapping filenames).

---
* find `-mtime` 

1. example 1:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -mtime -1
./technical/911report/chapter-1.txt
```
The purpose of this command is to find files in the current directory "technical" that I changed a day ago. It is useful because this command can help us find files modified by a specific day, just like finding chat records by date in social media. Even if we forget the specific file name or path, this method can easily search for it.

2. example 2:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -mtime -2
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
```
The purpose of this command is to find files in the current directory "technical" that I changed two days ago. It is useful because this command can help us find files modified by a specific day, just like finding chat records by date in social media. Even if we forget the specific file name or path, this method can easily search for it.

3. example 3:
```
maxiaoxiang@MacBook-Pro-7docsearch % find ./technical -mtime +1 -mtime -3
./technical/911report/chapter-1.txt
./technical/911report/chapter-2.txt
./technical/911report/chapter-3.txt
./technical/biomed/rr37.txt
./technical/government/Alcohol_Problems/Session1-PDF.txt
```
The purpose of this command is to find files in the current directory "technical" with a modification time of more than 1 day but not more than 3 days. It is useful because this command can help us find files modified by a specific day, just like finding chat records by date in social media. Even if we forget the specific file name or path, this method can easily search for it.