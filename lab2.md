Part 1:

This following code block is for StringServer.java:
```
import java.io.IOException;
import java.net.URI;

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    String message = "";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return String.format(message);
        } 
        else if (url.getPath().equals("/add-message")) {
            String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    message += "\n" + parameters[1];
            return String.format(message);
            } 
        }
            return "404 Not Found!";
        
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

```
and this following code block is for Server.java:
```
// A simple web server using Java's built-in HttpServer

// Examples from https://dzone.com/articles/simple-http-server-in-java were useful references

import java.io.IOException;
import java.io.OutputStream;
import java.net.InetSocketAddress;
import java.net.URI;

import com.sun.net.httpserver.HttpExchange;
import com.sun.net.httpserver.HttpHandler;
import com.sun.net.httpserver.HttpServer;

interface URLHandler {
    String handleRequest(URI url);
}

class ServerHttpHandler implements HttpHandler {
    URLHandler handler;
    ServerHttpHandler(URLHandler handler) {
      this.handler = handler;
    }
    public void handle(final HttpExchange exchange) throws IOException {
        // form return body after being handled by program
        try {
            String ret = handler.handleRequest(exchange.getRequestURI());
            // form the return string and write it on the browser
            exchange.sendResponseHeaders(200, ret.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(ret.getBytes());
            os.close();
        } catch(Exception e) {
            String response = e.toString();
            exchange.sendResponseHeaders(500, response.getBytes().length);
            OutputStream os = exchange.getResponseBody();
            os.write(response.getBytes());
            os.close();
        }
    }
}

public class Server {
    public static void start(int port, URLHandler handler) throws IOException {
        HttpServer server = HttpServer.create(new InetSocketAddress(port), 0);

        //create request entrypoint
        server.createContext("/", new ServerHttpHandler(handler));

        //start the server
        server.start();
        System.out.println("Server Started! Visit http://localhost:" + port + " to visit.");
    }
}
```

This is one case where I used ```/add-message```:   <br>    
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab3pic1.JPG)  <br>   

In this case, the main method in the StringServer class, the handleRequest method in the handler class, and the start method in the Server class are the methods called. The argument for the main method is the port number you input in the terminal when you run the StringServer class; in this case, it is 4000. The argument for the start method is the port number inputted into the terminal when running the StringServer class, 4000, as well as a new instance of the Handler method. The argument for the handle request method is the url you use for the website. When this is run, the port field in the StringServer class is intitalized to 4000, and the message field in the Handler class is changed from ```"ddd\ndddd"``` to ```"ddd\ndddd\nHow is it going"```

This is another case where I used ```/add-message```:   <br>    
![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/cs15l_lab3pic2.JPG)  <br>   

In this case, the main method in the StringServer class, the handleRequest method in the handler class, and the start method in the Server class are the methods called. The argument for the main method is the port number you input in the terminal when you run the StringServer class; in this case, it is 4000. The argument for the start method is the port number inputted into the terminal when running the StringServer class, 4000, as well as a new instance of the Handler method. The argument for the handle request method is the url you use for the website. When this is run, the port field in the StringServer class is intitalized to 4000, and the message field in the Handler class is changed from ```"ddd\ndddd\nHow is it going"``` to ```"ddd\ndddd\nHow is it going\nHellooo"```. 



Part 2:

testReverseInPlace:
* Failure inducing input = new int[] {1, 2, 3, 4}
* non-failure inducing input = new int[] {4, 3, 3, 4}    

In this screenshot, testReversedInPlace2 has the failure inducing input and testReversedInPlace3 has the non-failure inducing input

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab2pic3.JPG)

The symptom of the failure-inducing input test is that index 2 was actually 3 when expected to be 2. This is the two tests' outputs when run in the terminal

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab2pic4.JPG)

The bug was that the first half of list gets correctly reversed but when moving to second half of indices they attempted to take values from already updated positions which effectively left the second half identical to the first

the fix can be seen here:

![Image](https://raw.githubusercontent.com/AVGithub-1/cse15l-lab-reports/main/lab2pic5.JPG)

In this fix, a new empty array, copyArray is created first and the input array elements are copied to that array. Then, the input array is changed to be reversed by referencing the indices of copyArray so that values from the already updated input array aren't used.


Part 3:

Something I learned in lab2 that I didn't know before was how websites and queries for websites worked. The different parts of a website and starting a server was completely new to me and it gave me more of an understanding of how websites can change to different webpages and do different things like display new text. 





