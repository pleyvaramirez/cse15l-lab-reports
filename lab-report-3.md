# Lab Report 3 - Phillip Leyva Ramirez, PID: A17546555
# Part 1 - Bugs

For this part, we will examine the `reversed` method starting at line 14 in ArrayExamples.java from Lab 4. 

 ```
 static int[] reversed(int[] arr) {
      int[] newArray = new int[arr.length];
      for(int i = 0; i < arr.length; i += 1) {
          arr[i] = newArray[arr.length - i - 1];
      }
      return arr;
  }
```

1. Failure inducing input
```
 @Test
  public void testReversed2() {
    int[] input1 = {1, 2, 3};
    assertArrayEquals(new int[]{3, 2, 1}, ArrayExamples.reversed(input1));
    assertArrayEquals(new int[]{1, 2, 3}, input1);
  }
```

2. Input (no failure)
```
 @Test
  public void testReversed() {
    int[] input1 = { };
    assertArrayEquals(new int[]{ }, ArrayExamples.reversed(input1));
  }
  ```

4. JUnit Test Output
![Screenshot 2024-02-27 195006](https://github.com/pleyvaramirez/cse15l-lab-reports/assets/156385234/3099c32d-53ff-4ac2-9cd8-e7c965e0f450)


5. The purpose of the `reversed` method is to create a new array containing all the elements of the input array in reverse order. The method as it is currently written is not doing this. Although `newArray` is correctly defined, the method in the fourth line is actually replacing every element i in input array `arr` with its corresponding element in `newArray` . This is not correct because we want to fill up `newArray`. `arr` itself should remain unaltered by the method. Furthermore, the method returns the `arr` array, not `newArray`. Because we want a new array to be properly filled and returned, we also should swap every instance of `arr` with `newArray` and vice versa in the fourth and sixth lines:
```
  static int[] reversed(int[] arr) {
    int[] newArray = new int[arr.length];
    for(int i = 0; i < arr.length; i += 1) {
      newArray[i] = arr[arr.length - i - 1];
    }
    return newArray;
  }
```

# Part 2 - Researching Commands

