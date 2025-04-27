 # Implement a binary search to find the index of a string in a rotated sorted array of strings.

 Code :- 

 import java.util.*;

class findStringIndex {
    public static void main(String[] args) {
        String[] words = {"Kite", "Lion", "Monkey", "Apple", "Banana", "Cat", "Dog"};
        String target = "Banana";

        int index = findTheString(words, target);

        if (index != -1) {
            System.out.println(target + " found at index " + index);
        } else {
            System.out.println(target + " not found");
        }
    }

    public static int findTheString(String[] words, String target) {
        int start = 0;
        int end = words.length - 1;

        while (start <= end) {
            int mid = (start + end) / 2;

            if (words[mid].equals(target)) {
                return mid;
            }


            if (words[start].compareTo(words[mid]) <= 0) {

                if (words[start].compareTo(target) <= 0 && target.compareTo(words[mid]) < 0) {
                    end = mid - 1;
                } else {
                    start = mid + 1;
                }
            } else {
                if (words[mid].compareTo(target) < 0 && target.compareTo(words[end]) <= 0) {
                    start = mid + 1;
                } else {
                    end = mid - 1;
                }
            }
        }

        return -1;
    }
}

Output :-
Banana found at index 4

