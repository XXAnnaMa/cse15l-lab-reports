CSE15L - Week 3 Lab Report
Name: Xiaoxiang(Anna) Ma
Date: 10/30/2022

**Part 1**

Task: changing the name of the `start `parameter and its uses to `base`

1. Use `vim` to open the file
```
vim DocSearchServer.java
```

2. Use `/start<Enter>` to search the word `start` in code

![Image](2022-11-14%2009.25.16.png)

3. Use `ce base` to enter the insert mode, delete the word `start` and change it to `base`

![Image](2022-11-14%2009.41.00.png)

4. Use `<Esc>` to go back to the normal mode

（So far, we have only completed the modification of the first `start`.）

5. Press `n.` to find the next instance of `start` and replace it to `base`

![Image](2022-11-14%2009.52.01.png)

6. Do the same operation as step 5 to modify the last `start`

![Image](2022-11-14%2009.56.08.png)

7. Type `:wq` to save and exit vim

**Part 2**

* Editing on vim: 53 seconds (after a few times practice)
* Editing on VS Code: 1 minute 34 seconds

By comparing the two editing methods，I prefer to use vim because it has fewer steps and takes less time.

If the file needs to be changed less (three or less) I prefer to use vs code because I am more familiar with this way of doing things. But if the file needs to repeat the same operation many times, I prefer vim.
