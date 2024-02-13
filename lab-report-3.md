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

## Part 2 - Researching Commands
* -iname
  1. Example 1:
  2. Example 2:
* -type
  1. Example 1:
  2. Example 2:
* -user
  1. Example 1:
  2. Example 2:
* -size
  1. Example 1:
  2. Example 2:
  Source: [SnapShooter: Ultimate guide to Linux find command](https://snapshooter.com/learn/linux/find#:~:text=With%20the%20find%20command%2C%20you,in%20all%20Linux%20operating%20systems.)


