# Week 3 Lab Report 

## Part 1 -- Week 2 Lab 

***Code for the Simplest Search Engine:***
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;
//import java.util.List;
//import java.util.Arrays;

//printing an array 
class ArrayPrint{
    ArrayList<String> sr = new ArrayList<>();  
    ArrayPrint(ArrayList<String> sr){
        this.sr  = sr; 
        for(int i=0; i<sr.size(); i+=1){
            System.out.println(sr.get(i));
        }
    }
}

class Handler implements URLHandler {
    // The one bit of state on the server: a number that will be manipulated by
    // various requests.
    //ArrayList<String> str = new ArrayList<>(); 
    //ArrayList<String> con = new ArrayList<>(); 
    //ArrayList<String> sr = new ArrayList<>(); 
   
    //method to create String from ArrayList<String> 
    public String printString(ArrayList<String> sr){
        String r = String.join(", ", sr); 
        return r; 
    }
    ArrayList<String> str = new ArrayList<>();
    ArrayList<String> con = new ArrayList<>();
    
    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return "String: ";
        }
        else {
            System.out.println("Path: " + url.getPath());
            
            if (url.getPath().contains("/add")) {
                String[] parameters = url.getQuery().split("=");
                str.add(parameters[1]);
                return "String " + parameters[1]+ " added! It's now " + printString(str) + "size = " 
                + str.size();       
            } 
            else if (url.getPath().contains("/search")){
                String[] parameters = url.getQuery().split("="); 
                for(int i=0; i<str.size(); i+=1){
                        if(str.get(i).contains(parameters[1])){
                            con.add(str.get(i)); 
                        }
                    }
                return "String " + parameters[1] + " found! In the following words " + printString(con); 
            }
        }
        return "404 Not Found!";
    }
}

class SearchEngine {
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

## Screenshots of Application

1. 
In the screenshot above, I first added an instance of "okay" to the String ArrayList using the add method in my code ("/add?s=okay"). Once the code went through my argument, it filters through the argument to find the string I wanted to add, which in this case was "okay". This then updates the String ArrayList to contain "okay" and then prints out the whole string (which only contains okay at this point) on the screen. 

2. 
In the second screenshot, I aain added an instance of "" to the String ArrayList using the add method in my code ("/add?s=") a second time. This was to make it that the String ArrayList is longer for when we use the search method later. Similar to the previous screenshot, the code goes through the argument, filters through to find the string I wanted to add (""), and then updates the String ArrayList to contain "okay" and "". This updated list is then printed out onto the screen, showing the statement "". 

3. 
In the third screenshot, I this time tried to search for strings in the String ArrayList that contain the string "". This was done using the search method in my code ("/search?s="). Here, the code goes through the argyement and filters through the command to find the string that I want to look for in the list. It then goes through each String index in the list and, using another String Arraylist, only adds the strings in the original list that contain the inputted string. Once the code checks all indices, it prints out the new String Arraylist containing the specific string onto the screen. In our case, the original list had the strings "" and "", so when we looked for the string "" in the list, only one string, "", was returned since that was the only one containing the string "". 


## Part 2 -- Week 3 

***File One Name***
