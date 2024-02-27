# Minjoo O: CSE15L Lab Report 4

## Step 4: Log into ieng6
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/1a22915f-a7e3-45cf-8ef2-c1326f159507)
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/ca2602f8-60d8-4ba3-b7fd-f7a139374f58)
**Keys pressed:** `ssh<space>mo@ieng6.ucsd.edu<enter>` \
**Explanation:** I used the `ssh` command to log into `ieng6` with my account.

## Step 5: Clone fork using `SSH` URL
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/714ebbc9-4e99-47e1-beb1-b08cdc457dc4)
**Keys pressed:** `git<space>clone<space><cmd+v>`, `rm<space>-rf<space>lab7`, `<up><up><enter>` \
**Explanation:** I used `git clone` and copied + pasted the `SSH` URL to clone my fork, and then I got an error message saying
that `lab7` already exists. So, I removed the directory using `rm -rf lab7`, and then my previous `git clone` command
was 2 up in my history, so I had to press `<up>` two times and then `<enter>`.

## Step 6: Run tests to demonstrate that they fail
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/008ef993-0f36-4043-af55-0bc2c3453c72)
**Keys pressed:** `cd<space>lab7`, `bash<space>test.sh` \
**Explanation:** I had change directories to be in the `lab7` directory, so I did that using `cd`. Then. I ran the 
bash script using `bash test.sh` to run the tests to demonstrate that they fail.

## Step 7: Edit the code to fix the failing test
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/b9fa1b5d-b3ec-4571-bf71-c7d3f38decb6)

![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/7f9459ad-f1a0-4789-9670-a8d7ccf1c0d9)

**Keys pressed:** `vim<space>L<tab>.j<tab>`, `:$`, `7k`, `w`, `h`, `i`, `<delete>`, `2`, `<escape>`, `:wq`
**Explanation:** To open `ListExamples.java` in Vim, I used the `vim` command with `ListExamples.java`, using `<tab>` to
auto-fill the rest of the file name. Then, I used `:$` to quickly move to the end of the file so that I can more
easily access the line I need to edit. I moved up using `7k` (move up 7 times), `w` to skip to the `+` after `index1`, `h` to move
to the left one, `i` to enter insert mode, `<delete>` to delete `1`, and `2` to replace it. Then, I pressed `<escape>`
to exit insert mode, and then saved and exited Vim using `:wq`.

## Step 8: Run the tests to demonstrate that they pass

![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/687e737b-2dd6-4e3e-a124-d8f477555c0e)

**Keys pressed:** `<up><up><up><enter>` \
**Explanation:** Because I had the command `bash test.sh` 3 up in my command history, I pressed `<up>` three times
and then `<enter>`.

## Step 9: Commit and push the changes
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/d9db25b8-26a8-4952-8bcb-dbf701b3d6d2)
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/4fd55efd-643f-41c3-a5f7-67f92ea7fd3b)

**Keys pressed:** `git<space>commit<space>L<tab>`, `test<space>fixed`, `<escape>`, `:wq`, `git<space>push<space>origin<space>main` \
**Explanation:** To commit the changes to my Github account, I used the `git commit` command and typed in `L<tab>` to let
it auto-fill in `ListExamples.java` for me. Then, it took me to Vim to create a commit message, and I just typed in "test fixed", and then
`<escape>` to exit insert mode. Then, to save and exit vim, I used `:wq`, effectively committing the changes I made to
my GitHub account. To push the changes to `main` in my Github account, I used the `git push` command using `origin main` as the argument.
