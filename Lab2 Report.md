>PART ONE

The code for StringServer:


    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return printAll(list);
        }
        else {
            System.out.println("Path: " + url.getPath());
            if (url.getPath().contains("/add-message")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    list[list.length - 1] = parameters[1];   
                    return printAll(list);
                }
            }
            return "404 Not Found!";
        }
    }

    public String printAll(String[] x){
        String out ="";
        for(int i = 0; i < x.length; i+=1){
            out = out + x[i] + "\n";
        }
        list = (String[])resizeArray(list, list.length+1);
        return out;
    }


    //this code below is from internet, the purpose of this code is just change the size of the Array
    private static Object resizeArray (Object oldArray, int newSize) {
            int oldSize = java.lang.reflect.Array.getLength(oldArray);
            Class elementType = oldArray.getClass().getComponentType();
            Object newArray = java.lang.reflect.Array.newInstance(elementType, newSize);
            int preserveLength = Math.min(oldSize, newSize);
               if (preserveLength > 0)
                  System.arraycopy(oldArray, 0, newArray, 0, preserveLength);
            return newArray;
      }


![image](https://user-images.githubusercontent.com/71479254/215657068-2a22f86f-45d3-498d-9a95-5981e9b9e95e.png)

In this screenshot, The method "handlerequest" is been called. Since it has /add-message, it will call the "resizeArray" method to increment the size of the array, and also call the "printAll" method to print out all the string in this array.

![image](https://user-images.githubusercontent.com/71479254/215657686-6fbca17b-eedd-4c79-8ce5-3eec0089dfa5.png)

In this screenshot, it also called the same three methods, and this request extend the size of list. list is just a array that stores all the strings. I appended the new string "How are you" at the end of the array and increment the size of the array.

Here the value of the **list** changed, it stored one more string. The parameter changed since we have a different word behind add-message. The url of course changed since we need to change that to make another request.

>PART TWO

For the Array example in lab3, One failure-including input of the function ReverseInPlace would be {3,2,1,0}. 

    @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3, 2, 1, 0 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 0, 1, 2, 3 }, input1);
	}

and the JUnit test returns

    1) testReverseInPlace(ArrayTests)
    arrays first differed at element [2]; expected:<2> but was:<1>
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:78)
        at org.junit.internal.ComparisonCriteria.arrayEquals(ComparisonCriteria.java:28)
        at org.junit.Assert.internalArrayEquals(Assert.java:534)
        at org.junit.Assert.assertArrayEquals(Assert.java:418)
        at org.junit.Assert.assertArrayEquals(Assert.java:429)
        at ArrayTests.testReverseInPlace(ArrayTests.java:9)
        ... 32 trimmed

One input that doesn't induce a failure would be:

    @Test 
	public void testReverseInPlace() {
    int[] input1 = { 3,3,3 };
    ArrayExamples.reverseInPlace(input1);
    assertArrayEquals(new int[]{ 3,3,3 }, input1);
	}
    
 And JUnit test returns 
 
    JUnit version 4.13.2
    .
    Time: 0.008

    OK (1 test)
 
 And the symptom that JUnit test has found also shown above.
 
 The code before fixing the bug:
 
    static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
            arr[i] = arr[arr.length - i - 1];
        }
    }
    
The code after fixes the bug:

    static void reverseInPlace(int[] arr) {
        for(int i = 0; i < arr.length; i += 1) {
           int temp = arr[i];
           arr[i] = arr[arr.length - i - 1];
           arr[arr.length - i - 1] = temp;
        }
    }  
    
 The main issue of the previous code is it updated the number in the front, but it also lose the data of the first half of the array. So instead of directly assign the arr[i], we swap the number at arr[i] and arr[arr.length-1-i]. Therefore we don't lose data, and be able to reverse an array correctly.
 
 >PART THREE
 
These two labs have taught me a lot of things. The second lab taught me how to build a server, I learned how to create a local server and change the role of the server in the backend. I also learned how to set up a remote server where I can modify the numbers in other people's servers. This taught me a lot. The third lab taught me how to fix bugs, which will be very useful in my future work. Here I used junit test to find the problem. I learned to use google's gtest before, also has the same effect, are very good to use. I didn't know any of this before so it is really helpful.
