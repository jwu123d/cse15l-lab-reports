The code for StringServer:
'''
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String list[] = {""};

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
}

class StringServer {
    public static void main(String[] args) throws IOException {
        if(args.length == 0){
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }

        int port = Integer.parseInt(args[0]);

        Server.start(port, new Handler());
    }
}
'''
