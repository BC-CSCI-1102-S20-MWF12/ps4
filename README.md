# Problem Set 4
## Due Monday, February 10 at 11:59pm

---

This problem set has two components: (1) completing an incomplete linked list implementation of a stack ADT; and (2) using that implementation to case-insensitively sort an array of words in reverse alphabetical order. You will have the opportunity to write a bit of your own linked list code and you will discover an application of the stack ADT.

In the `src` directory, you will find three files:

* `Stack.java` An interface for a stack of strings, similar to the one we've seen in class.
* `StackLL.java` An incomplete implementation of the `Stack` interface
* `ReverseAlphabetizer.java` An incomplete class that uses `StackLL` to put the words in a string into alphabetical order.

---

## Part 1
In this part of the problem set, you will be writing `toString()`, the missing method in `StackLL.java`. If you look in the   `StackLL.java` file, you will see commented code. Near the bottom of the file you'll see the words `YOUR CODE GOES HERE`. This is the only place in this file where you need to write any code. 

There are a number of ways you could write this, but I have provided an algorithm that will be easy to implement. These instructions are also included in the `.java` file itself.

1. Create a `StringBuilder` object.
2. Traverse the linked list using a for loop as we have demonstrated in class.
3. As you visit each node, append the item to the `StringBuilder` object followed by a single space.
4. Return the `StringBuilder` object as a String, calling its `toString()` method.

## Part 2
In this part of the problem set, you will be working on the `ReverseAlphabetizer.java` class, which uses two instances of `StringLL` to alphabetize a string of words. Open the file `ReverseAlphabetizer.java` and you will see that I have provided some basic code for you. All of your code will go in the `main()` method. You do not need to write additional methods.

### Comparing two `String` objects
To help you figure out the correct alphabetical order of two strings, you will be using the `compareTo()` method that comes built-in with the `String` class. You do not need to write this method. You just need to call this method and interpret its output. The `compareTo()` method of `String` returns a positive number if the calling String comes after the argument String in the alphabet; a negative number if the calling String comes before the argument String in the alphabet; and 0 if the two Strings are the same. Example:

```java
String s1 = "animal";
String s2 = "zoo";

System.out.println(s1.compareTo(s2)); // will print -25 because "animal" (s1) comes before "zoo" (s2)
System.out.println(s2.compareTo(s1)); // will print 25 because "zoo" (s2) comes after "animal" (s1)
System.out.println(s1.compareTo("zoo")); // will print 0 because "zoo" (s1) is the same as "zoo"
 ```

### Running the program
Much to the delight of many of you, we will be using the  `Scanner` class to read in a string from the user during execution of this program. (Recall that previously I was asking you to use command line arguments, i.e., the arguments to main(), i.e., the stuff you would type after the class name when running the program.) I've included the code for using `Scanner` in the `ReverseAlphabetizer.java` file. 

When you run the program you'll just type `java ReverseAlphabetizer` with no arguments. You will then be prompted to enter a string of words. When you hit `return`, the program will process the string you entered.

This is a sample of how we will be running the code when we test your submission:

<img src="output.png" width="600"  />


### The algorithm
Create two `StackLL` objects: one called `mainstack` for storing the reverse alphabetized list of words, and one called `tempstack` for temporarily offloading words fom `mainstack` while you search for the proper location for the incoming word.

This is how the algorithm works. Write a for-loop to go through each word in the array of words from the input string. For each word `w`:

* Peek at the top word of `mainstack`. Let's call it `top`. 

* While `top` comes before `w` in the alphabet (use the `compareTo()` method on `String` to determine this!), pop `top` off `mainstack` and push it on to `tempstack`. Reset `top` to whatever `peek` returns.

* When `top` finally comes after `w` alphabetically, push `w` onto `mainstack`.

* Then `pop` each element off of `tempstack` and push onto `mainstack`.

* Continue to the next word in the array of words to sort until you have sorted the whole array.

When you are done, you should have a sorted stack of words in `mainstack`, ordered alphabetically (A to Z) from top to bottom. The stack `tempstack` should be empty. Print out the original input `String` followed by the sorted stack (using `toString()`) to prove that your code works correctly.


### Some hints and notes

* In your implementation of the sorting algorithm, you will **need** to include one or more checks on the stacks using `isEmpty()`. For instance, if a stack is empty, you shouldn't call `peek()` or `pop()`. If you get a null pointer exception (or worse yet, an infinite loop!), it might be because you are calling `peek()` or `pop()` on an empty stack.

* The `compareTo()` method in String is *case sensitive*. That is, capitalized words will always come before uncapitalized words. Thus, if your string is "Boston baseball Commonwealth chestnut", the stack will be sorted, from top to bottom as "Boston Commonwealth baseball chestnut".

* You should frequently use the `toString()` method you implemented in `StackLL` to check on the contents of your stacks.

* All of your code should go in the `main()` method. You do not need to write additional methods, and you do not need any external variables.

### Pushing and verifying your submission

Once your code works to your satisfaction, push `StackLL` and `ReverseAlphabetizer.java` to your personal master repo on the GitHub Classroom site, as you did for previous problem set. Use the commit message "READY FOR GRADING" so we know you are done. 

As always, you can check to see if it worked by going to your account on GitHub and checking to see if it was updated and whether the files have changed in the way you expected. This is your responsibility.

---

## Important notes on grading

1. The only acceptable way to submit is through GitHub. If you do not submit via GitHub, you will get a 0.

2. The `StackLL.java` and `ReverseAlphabetizer.java` file **must be in the `src` directory**. You will lose 2 points for each file that is in the wrong directory. The best way to make sure they are in the right place is to never ever move them in the first place.

3. Your code must compile. If a class does not compile, you will get a 0 for that class. If you are struggling and you aren't able to get in touch with me or the TAs, any TAs in the lab can help you compile your code.


