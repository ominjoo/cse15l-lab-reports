# Minjoo O: CSE15L Lab Report 3

## Part 1 - Bugs

**Failure-Inducing Input (JUnit test)**
```
  @Test
  public void testReverseInPlace() {
    int[] input1 = {3, 4, 5}; // failure-inducing input
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{5, 4, 3}, input1);
  }
```
**Non-Failure-Inducing Input (JUnit test)**
```
  @Test
  public void testReverseInPlaceOne() {
    int[] input1 = {3}; // input that DOESN'T induce failure
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{3}, input1);
  }
```
**The Symptom (output of jUnit tests):**
![image](https://github.com/ominjoo/cse15l-lab-reports/assets/149638043/bdca3739-b5be-4d11-a5fa-aaf00b1a65f3)

**The Bug** \
Before:
```
  static void reverseInPlace(int[] arr) {
    for(int i = 0; i < arr.length; i += 1) {
      arr[i] = arr[arr.length - i - 1];
    }
  }
```
After:
```
  static void reverseInPlace(int[] arr) {
    int[] temp = new int[3];
    for(int i = 0; i < arr.length; i += 1) {
      temp[i] = arr[arr.length - i - 1];
    }

    for (int i = 0; i < arr.length; i += 1){
      arr[i] = temp[i];
    }
  
  }
```
The bug in the code was that the loop is directly updating the contents of the input array as it is being reversed, so updated elements end up being used for elements at later indices. To fix the bug, a temporary array must be created in order to store the elements of the original array. Then, after the reversal of the temporary array, the contents of the original input array should be replaced by the contents of the temporary array. If not, the element at index 0 can be switched with the element at the end of the array, and then when the loop approaches the end of the array, the element at the end will not change. This is why the input of an array of {3, 4, 5} produces {5, 4, 5}. 

## Part 2 - Researching Commands: `find`
## `-iname`
* **Example 1:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -iname 'draftrecom-pdf.txt'
./government/Alcohol_Problems/DraftRecom-PDF.txt
```
`-iname` is an option we can use when we don't exactly know how the letters within the filename are capitalized. Unlike with `-name`, `-iname` is case *insensitive*, so we don't need to know how a file name is capitalized when we want to find its location in `./technical`.
* **Example 2:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -iname '*report*txt' 
./government/About_LSC/Progress_report.txt
./government/About_LSC/Strategic_report.txt
./government/About_LSC/Special_report_to_congress.txt
./government/About_LSC/commission_report.txt
./government/About_LSC/reporting_system.txt
./government/About_LSC/State_Planning_Report.txt
./government/About_LSC/State_Planning_Special_Report.txt
./government/Post_Rate_Comm/ReportToCongress2002WEB.txt
```
This time, the `find` is used with `-iname` to find where in `./technical` a certain file when we only have a general idea was what it's called, or the words it contains. This is different from using `-name`, which requires you to know the exact spelling, format, and capitalization of the filename - which may not always be the case in reality. \

Source: [RedHat: 10 ways to use the Linux find command](https://www.redhat.com/sysadmin/linux-find-command)

---
## `-type`
* **Example 1:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -type d
.
./government
./government/About_LSC
./government/Env_Prot_Agen
./government/Alcohol_Problems
./government/Gen_Account_Office
./government/Post_Rate_Comm
./government/Media
./plos
./biomed
./911report
```
When used with type `d`, this is useful when you don't want to list the files in the given path but want to list items based on their type, such as directories. Using `-type d` lists the directories within `./technical.`
* **Example 2:**
```
minjooo@Minjoos-MacBook-Pro technical % find ./911report -type f
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-13.1.txt
./911report/chapter-13.2.txt
./911report/chapter-13.3.txt
./911report/chapter-3.txt
./911report/chapter-2.txt
./911report/chapter-1.txt
./911report/chapter-5.txt
./911report/chapter-6.txt
./911report/chapter-7.txt
./911report/chapter-9.txt
./911report/chapter-8.txt
./911report/preface.txt
./911report/chapter-12.txt
./911report/chapter-10.txt
./911report/chapter-11.txt
```
When used with type `f`, you can see a comprehensive list of all the files, and no directories, within a certain path/directory. This can be used when you want to see how many files are in a directory, find a file you can't remember the name of, etc.

Source: Source: [RedHat: 10 ways to use the Linux find command](https://www.redhat.com/sysadmin/linux-find-command)

---
## `-exec`
* **Example 1:**
```
minjooo@Minjoos-MacBook-Pro technical % find ./government/Media -name 'agency_expands.txt'
./government/Media/agency_expands.txt
minjooo@Minjoos-MacBook-Pro technical % find ./government/Media -name 'agency_expands.txt' -exec rm {} \; 
minjooo@Minjoos-MacBook-Pro technical % find ./government/Media -name 'agency_expands.txt`

```
The `-exec` option can be used to execute commands on files retrieved by `find`, such as deleting a found file using `-exec rm {} \;`. This is useful for when you need to manage and delete files from the command line. As shown above, the file `agency_expands.txt` has been deleted.
* **Example 2:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -name 'commission_report.txt' 
./government/About_LSC/commission_report.txt
minjooo@Minjoos-MacBook-Pro technical % find . -name 'commission_report.txt' -exec mv {} ./biomed \;
minjooo@Minjoos-MacBook-Pro technical % find . -name 'commission_report.txt'                 
./biomed/commission_report.txt
```
The `-exec` option can be used to move found files to a different directory from the command line using `-exec mv {} <path> \;`. In this example, the file `commission_report.txt` was moved from `./technical/government/About_LSC` to `./biomed` \

Source: [TechAdmin: Find Command in Linux with Practical Examples](https://snapshooter.com/learn/linux/find#:~:text=With%20the%20find%20command%2C%20you,in%20all%20Linux%20operating%20systems.](https://tecadmin.net/linux-find-command-with-examples/)https://tecadmin.net/linux-find-command-with-examples/)

---
## `-size`
* **Example 1:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -size +200kb
./government/Env_Prot_Agen/bill.txt
./government/Gen_Account_Office/GovernmentAuditingStandards_yb2002ed.txt
./government/Gen_Account_Office/Statements_Feb28-1997_volume.txt
./government/Gen_Account_Office/d01591sp.txt
./biomed/commission_report.txt
./911report/chapter-13.4.txt
./911report/chapter-13.5.txt
./911report/chapter-3.txt
```
We can use the `-size` option to recursively search for files within `./technical` that are bigger or less than a certain file size. In this case, we searched for files that are bigger than 200 kilobytes. This is useful when you want to access files of a certain size or filter files by size for organization purposes, etc.
* **Example 2:**
```
minjooo@Minjoos-MacBook-Pro technical % find . -size 118656c
./911report/chapter-1.txt
```
We can use the `-size` option to recursively search for files within `./technical` that are exactly a given file size. In this case, we searched for files that are exactly 118,656 bytes. This is useful when you want to access files of a certain size or filter files by size for organization purposes, etc.

Source: [TechAdmin: Find Command in Linux with Practical Examples](https://snapshooter.com/learn/linux/find#:~:text=With%20the%20find%20command%2C%20you,in%20all%20Linux%20operating%20systems.](https://tecadmin.net/linux-find-command-with-examples/)https://tecadmin.net/linux-find-command-with-examples/)


