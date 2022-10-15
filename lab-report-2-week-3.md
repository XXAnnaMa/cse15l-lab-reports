CSE15L - Week 3 Lab Report
Name: Xiaoxiang(Anna) Ma
Date: 10/14/2022

## Part 1

file: SearchEngine.java
```
import java.io.IOException;
import java.net.URI;
import java.util.ArrayList;

class Handler implements URLHandler
{
    ArrayList<String> strlist = new ArrayList<>();
    String str = "Nothing Show Off!";

    public String handleRequest(URI url) {
        if (url.getPath().equals("/")) {
            return str;
        } 
        else{
            System.out.println("Path: " + url.getPath());
            if (url.getPath().equals("/add")) {
                String[] parameters = url.getQuery().split("=");
                if (parameters[0].equals("s")) {
                    strlist.add(parameters[1]);

                    return String.format("%s has already been added", parameters[1]);
                }
            }
            else if (url.getPath().equals("/search")) 
            {
                System.out.println("Path: " + url.getPath());
                if (url.getPath().contains("/search")){
                  String[] parameters = url.getQuery().split("=");
                  
                  if (parameters[0].equals("s")){
                      ArrayList<String> list = new ArrayList<>();
                      for (String e: strlist){
                        if (e.contains(parameters[1]))
                            list.add(e);
                      }
                        return String.format("" + list);
                    }
                  }
                }
            }
            return "404 Not Found!";
        }
}    

class SearchEngine
{
    public static void main(String[] args) throws IOException
    {
        if(args.length == 0)
        {
            System.out.println("Missing port number! Try any number between 1024 to 49151");
            return;
        }
        int port = Integer.parseInt(args[0]);
        Server.start(port, new Handler());
    }
}
```

![Image](2022-10-14%2019.47.07.png)

The method “handleRequest(URL url)” is called.

The value of argument("url") is "/". Initially, additional fields can be added to raise references to other functions such as add and search.

The value of field("str") is "Nothing Show Off!". Changing the value of "str" will make the argument "/" (or empty) different characters like on the web page.

![Image](2022-10-14%2019.06.08.png)

The method “handleRequest(URL url)” is called.

The value of arguments("url") are "/add?s=apple" . Change the fields after "/add?s=" to add different elements into the array list.

The value of fields "parameters" and "strlist" is "apple" . Until the input (field) of this part is changed (that is, the complete process), the returned result will not have any change.
The screenshot below is the result of converting this value to "pineapple".
![Image](2022-10-14%2019.06.22.png)


![Image](2022-10-14%2019.07.06.png)

The method “handleRequest(URL url)” is called.

The value of arguments("url") are "/search?s=app" . Changing fields after "/search?s=" will return a different array list on the web page.

The value of fields "parameters" and "list" is "app" . Entering a different field values will find the elements that meet the requirements in the array list where other fields have been added before and return it.



## Part 2

-Array Methods-

in ArrayTests.java
The failure-inducing input(the code of the test):
![Image](2022-10-14%2017.28.08.png)

The symptom (the failing test output):

"array first differed at element [0]; expect:<3> but was: <0>." My expect out put is{3, 2, 1}, but the actual output is {0, 0, 0}.

The bug is,
![Image](2022-10-14%2017.42.54.png)
row 17: (arr[i] = newArray[arr.length - i - 1]) 

The fixed method:
![Image](2022-10-14%2017.49.36.png)

Explaination:
The bug assigns an all-zero value of newArray to the original array and also return old array, causing the output array to be an all-zero array.

----

-List Methods-

in ListTests.java
The failure-inducing input(the code of the test):
![Image](2022-10-14%2018.03.26.png)

The symptom (the failing test output):

"arrays first differed at element [0]; expected:<[abcde1]> was: <[abcdefghi11]>." 

The bug is,
![Image](2022-10-14%2018.03.44.png)

(I wrote the comment "shoud delete 0" after the bug.)

The fixed method:
![Image](2022-10-14%2018.03.57.png)

Explaination:
In the filter method, if filter is true will add the element at index0 to the result. Therefore, elements that meet the requirements (number of characters greater than five) will continue to be added to index0 and the next element will always replace the previous one, which eventually results in only one element in the result of return.

