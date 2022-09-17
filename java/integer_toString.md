---
title: Integer.toString(int i, int radix)
parent: Java
has_children: false
---
Date: 17 Sep 2022

# Integer.toString(int i, int radix)
To convert Integer to String with specifying base: Integer.toString(number, base) func is used.

## Example
```java
// Leetcode 2396: Strictly Palindromic Number
class Solution {
    public boolean isStrictlyPalindromic(int n) {
        boolean flag = true;
        for (int i = 2; i < n -1; i++) {
            if (!check(Integer.toString(n, i))) {
                flag = false;
                break;
            }
        }
        return flag;
    }

    public boolean check(String n) {
        int left = 0;
        int right = n.length() - 1;
        while (left < right) {
            if (n.charAt(left) != n.charAt(right))
                return false;
            left++;
            right--;
        }
        return true;
    }
}
```
## Now think about this
Suppose if you want have to convert a number like 100000 to base 50001. The first digit is a 1, but the second digit has to represent 49999. That is, what does `Integer.toString(100000, 50001) return? **Strangely, it returns 100000**. Clearly that's not right! It should be a two-digit number. Something like 1X where X is some symbol that represents 49999. 

Why dit it return `100000` instead?

The javadoc for Integer.toString(int, int) is interesting and tells us the answer:

```java
public static String toString(int i, int radix)

// Returns a string representation of the fitst argument in the radix specified by the second argument.

// If the radix is smaller than Character.MIN_RADIX or larger than Character.MAX_RADIX, then the radix 10 is used instead.
```
Character.MAX_RADIX = 36
But the problem starts here, the leetcode problem allows n to 10^5, so the radix could be as high as 99998. If I am reading the javadoc right, this means Integer.toString(n, i) will silently do the worng thing (use base 10) when i is 37 or greater. That explains why `Integer.toString(100000, 50001)` returns 100000. So I think you may need to provide your own method to convert to base i. I'm not sure why Java would quietly use base 10 instead of throwing an IllegalArgumentException; it's kind if an unfortunate trap they have set for people using this method.

I wonder if it would be best because of potentially large bases to use an int[] to represent the number in base i, rather than a char[] or String. Because chars only can hold 2^16 values (65536). Some of them are even special values. So we can't represent numbers in bases like 99998 using characters. But we could using int[] where each element of the array is the decimal value of the digit in base i, not the actual digit in base i (because, what digit do we use to represent e.g. 49999?). For example, if we had 100000 in base 50001, we would write it as the int[] { 1, 49999 }. Here's an update to your solution that does this. (Maybe it'd be more efficient to leave it as a List instead of int[], but this works).

```java
class Solution {
    public boolean isStrictlyPalindromic(int n) {
        boolean flag = true;
        for (int i = 2; i < n - 1; i++) {
            if (!check(toBase(n, i))) {
                flag = false;
                break;
            }
        }
        return flag;
    }

    public boolean check(int[] n) {
        int left = 0;
        int right = n.length - 1;
        while (left < right) {
            if (n[left] != n[right])
                return false;
            left++;
            right--;
        }
        return true;
    }

    public int[] toBase(int n, int base) {
        int remaining = n;
        List<Integer> digits = new LinkedList<>();
        while (remaining > 0) {
            digits.add(0, remaining % base);
            remaining = remaining / base;
        }
        return digits.stream().mapToInt(Integer::isValue).toArray();
    }
}
```

It turns out that no number between 1 and 100000 is palindromic in all bases 2 through min(36, n - 2), so our code still produces the correct answer. But I think for the wrong reason, thanks to Java's unfortunate choice to make radix default to 10 if you give it a value greater than 36.
