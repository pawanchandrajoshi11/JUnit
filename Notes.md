# JUnit - Notes

Junit is a unit testing framework for java programming language.

**adv:**

- Seperate your tests from your code.
- no need for main() method
- makes sure new code doesn't break existing code (regression testing)


<h2>Junit fundamentals</h2>

@Test

> Junit method is a method contained in a class which is used for testing, to define certain method is a test method we use `@Test` before it.

- assertEquals, assertNotEquals
```java
import org.junit.*;
public class Test{

    @Test
    public void test1(){
        assertEquals(2, 2); //true
        Assert.assertEquals(3, 3); //true
        // both formats will work fine
        assertEquals(expected, actual);

        assertEquals(4, 5); //false
        assertEquals("Hello", "hello"); //false
    }

    @Test
    public void test2(){
        assertNotEquals(3, 4); //true
        assertNotEquals(2, 2); //false
    }
}
```

- assertTrue(), assertFalse()

```java
import org.junit.*;
public class Test{

    @Test
    public void test1(){
        assertTrue(true); //true
        assertTrue(false); //false
        assertTrue("abc".length() == 3); //true
    }

    @Test
    public void test2(){
        assertFalse(true); //false
        assertFalse(false); //true
    }

```

**Coding Exercise**

```java
import org.junit.*;
public class Test{
    int x = 2;
    int y = 2;
    int z = 3;

    // write a test method with an assert that shows x and y are equal to eachother
    @Test
    public void test1(){
        assertEquals(x, y); //true
    }

    // write a test method with an assert that shows y and z are not equal to each other
    @Test
    public void test2(){
        assertNotEquals(y, z); //true
    }

    // write a test method with an assert that shows a is true and b is not true
    boolean a = (x == y);
    boolean b = (y == z);

    @Test
    public void test(){
        assertTrue(a); //true
        assertFalse(b); //true
    }
}
```
---

<h3>Bug fix Process</h3>


1. Create a Junit test that triggers the bug, (you want a  fail condition ironically, that shows you found a bug).
2. Fix the bug in the source code.
3. Run your junit test **again** and get a green bar/check/tick. This shows you fixed the bug.
4. Submit your updated source code and your junit test(s) to github for code review by your tech lead.

---

<h3>Feature Request Process (test - driven development)</h3>

1. Create an empty method that does nothing (have it throw an exception etc.).
2. Write junit tests that properly exercise the methods.
3. Run the junit tests, They will fail initially because the source code method has not yet been implemented.
4. Write and refine the source code method until until all of your junit tests pass.
5. Submit your updated source code and your junit test(s) to github for code review by your tech lead.

---

@BeforeAll, @AfterAll annotations

```java

public class Test{
    @BeforeAll
    public static void setup(){
        system.out.println("first");
    }

    @AfterAll
    public static void tearDown(){
        system.out.println("last");
    }

    @Test
    public void test1(){
        system.out.println("now running test 1");
    }

    @Test
    public void test1(){
        system.out.println("now running test 2");
    }
}
```
output:

```
first
now running test 1
now running test 2
last
```
---

- assertArrayEquals

```java
public class Test{
    @Test
    public void test(){
        int arr1 = {1, 2, 3};
        int arr2 = {1, 2, 3};
        int arr3 = {3, 4, 5, 6};
        int arr4 = {6, 7, 8, 9};

        assertArrayEquals(arr1, arr2);  //true - same length, same elements
        assertArrayEquals(arr2, arr3);  //false - different length
        assertArrayEquals(arr3, arr4);  //false - same length but different elements
    }
}
```

# END