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

