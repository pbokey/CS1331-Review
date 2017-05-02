# Final Exam Review

## Notes
1. vars, expressions, assignment
    * ops
    ````Java
    public static void main {
        int x = 9;
        double y = 8.7;
        String z = "Pranav";
        char c = "B";
        double x + y = 16.7; //you always cast up never cast down to something more general
        //all ints can be doubles but not all doubles are ints
    }
    ````
    * precedence
2. Strings - text manipulation
    * I/O
    ````Java
    import java.util.Scanner;

    public static void main(String[] args) {
        Scanner x = new Scanner(System.in);
        System.out.println("Enter a String: ");
        String input = x.nextLine();
        input += " this is how you concatonate a string in java."
        System.out.println(input)
        int len = input.length;
    }
    ````
3. Control Flow
    * Conditionals
    ````Java
    public static main(String[] args) {
        if (some condition) {
            \\execute some command
        } else if (some other command) {
            \\execute some other command
        } else \\neither of those conditions were met {
            \\execute some last command
        }
        char c = "c";
        switch(c):
        case a:
            print(5)
        case b:
        case c:
            print(10) //will print this cause case c is triggered
        default: //not required
            print("Did not find it")
    }
    ````
    * Iteration
    ````Java
    public static main(String[] args) {
        //for loop
        for (int x = 0; x < 10; x++) {
            System.out.println(x + "\n"); \\1,2,..,9
        }
        int x = 0
        while (x < 10) {
            System.out.println(x + "\n"); //0,1,...,9
            x++; //must have an incrementer so that x approaches the while condition
        }
        int y = 0
        do {
            System.out.println("Doing \n"); //going to print Doing 10 times
            y++;
        } while (y < 10);
    }
    ````

4. Math, Random #'s
    * Random Class
    ````Java
    import java.util.Random;

    public static main (String[] args) {
        Random num = new Random(5) //in the arguments is where a seed would go, using the same seed will yield the same sequence of numbers every time you run the program
        Random x = new Random() //leaving the seed empty means that the numbers generated are random
        int rand1 = x.nextInt(5) + 1 //will give me a random number 1 -> 5 inclusive
        int rand2 = x.nextInt(5) //will give me a random number 0 -> 4 inclusive
        double rand3 = x.nextDouble() //this function takes no arguments and returns a number between 0 and 1, multiply by a factor to return your desired number
        //example
        double rand4 = x.nextDouble() * 6 //will return a number between 0 and 6 exclusive
    }
    ````
    * Check if two doubles are equal or not
      ````Java
      double a = 1.00000000000001
      double b = 0.99999999
      //if you want these two to be equal
      return Math.abs(a - b) < 1e-6;
5. Arrays - 1D, MultiDimensional
    ````Java
    public static main(String[] args) {
        int[] intArray = new int(5); //an array of a primitive type
        String[] stringArray = new String(5); //an array of a String object type
        Object[] objectArray = new Object(5); //an array of a random object
        //all these arrays are filled with a "null" object until you manually add stuff to the array
        int[] intArray2; //you can also declare an array with this, it has not been instantiated
        int[] intArray3 = {1, 2, 3, 4, 5, 6, 7, 8}; //this array is now made and filled, its size is 8 and this cannot be changed

        intArray3[0] = 10; //the first element in the array is now 10
        intArray.length; //this will return 5, length is a property of an array not a method
        for (int x: intArray3) { //syntax of a for-each loop
            print(x); 
        }
    ````
    * Copying Arrays
    ````Java
    int[] intArray4 = intArray3; \\this variable is pointing to the same array in memory as intArray3
    System.arraycopt(source, srcPos, targetArray, tarpos, length); //srcPos and tarpos are the starting points in each respective array
    System.arraycopy(sourceArray, 0, targetArray, 0, length);
    ````
    * Two Dimensional Array
    ````Java
    int[][] twoDArray = new int[2][4]; //the first number is the row and the next number is the column
    for (int[] x: twoDArray) {
        //the first iteration will go through each row which is another array
        for (int y: x) {
            print(x); //this will print all the items in the array
        }
    }
    ````
    * variable length arguments
    ````Java
    public static variableDouble(double... numbers) { //there can only be one variable length paramter in a method, and this needs to be the last parameter declared in the method
        if (numbers.length == 0) {
            System.out.println("You passed in no arguments");
        }
    }
    ````
6. Classes + Objects
    1. Methods, parameters, constructors
    ````Java
    public class Review {
        //these are instance data that each instantiation of this class (an object) has
        //all these data are private so only this class can see
        private int timeStudy;
        private double java;
        private String topic;

        public Review() {

        }
        //when you write a argument constructor the no-args constructor is automatically overriden, if you dont include a default cosntructor and just write an argument constructor then you can never call the default constructor
        public Review(int time, double j, String t) {
            this.timeStudy = time;
            this.java = j;
            this.topic = t;
        }
    }
    ````
    2. Instance data, visibility
    ````Java
    public class Review {
        protected int data; //everything that imports this class and is in the same package as this can see
        private int[] datum; //only this class can access this data
        public String everyoneCanSee;
        private static int count; //this count variable will be the same for every object that is instantiated of this class, this is because static data are class data not instance data
    }
    ````
    3. Static data + methods
        * static methods are methods that are class methods, meaning instead of saying object.method(), you use classname.method() to call them
        * static data is shared across all instantiations of the class, because it is associted with the class not with the object
        * For example the main method is static because you can call the method without creating an instantiation of the the object that main class you are in represents
7. Software Development
    1. Debugging, Testing
        * You can use the IDE to manually debug the problem to see what is wrong
        * You can also use Print statements in the code to see what is happening
        * You can use Unit Tests, and JUnits, to use code to check
    2. IDEs
        * For Software development
        * Makes it easier, autocomplete, etc. 
    3. Packages
        * Package helps organize code and reduce name-conflicts
        ```Java
        package example;

        public class MemberOfPackage {
            //some code
        }
        ````
        ````Java
        import example.*;
        
        public class NewStuff {
            MemberOfPackage ex = new MemberOfPackage(); //this is a valid statement
        }
        ````
    4. JavaDocs
        * helpful documentation that tells the user what everything in a program is
8. Inheritance
    * Subclassing
        ````Java
        public class Parent {
            private int data;

            public void meth1(){

            }
            public void meth2() {

            }

            public int getData() {
                return this.data
            }

            public void setData(int d) {
                this.data = d;
            }
        }
        ````
        ````Java
        public class Child extends Parent {
            //this class inherits all the data and methods from the Parent class
            //this class inherits the private data, but it is not visible in this class
            //this is why you have getters and setters
        }
        ````
        * constructor chaining is very important concept
        * if there is no explicit call to a super constructor in a child class, it will automatically call the super() **No Args Constructor**
        * if there is an explicit call, it will just execture the code

    * Overriding
        * a method with the same name and same method signature (**same parameters**) as another method is said to be **overriden**
        * a method with the same name but different method signature (**different parameters**) as another method is said to **overloaded**
    * Hierrarchies
9. Object
    * toString
        * By default toString just returns the memory location of the object
        * you want to override this method to provide your own toString method that is more easily understood by the user
        ````Java
        public class Example {
            private int data;
            private String name;
            private double score;

            //constructors, methods, etc.

            public String toString() {
                //this overrides the Object class toString() method
                return name + "has ID: " + data + ", and a score of: " + score;
            }
        }
        ````
    * equals
        * it is the same idea for the equals method
        * if the two memory locations of an object are equal than this default method returns true; however you want to override this method because it needs to be true whenever some data of the two objects are true
        ````Java
        public class OverrideEquals {
            private int data;
            private String name;

            //usual class code here

            public boolean equals(Object o) {
                //this overrides the equals method in the Object class
                if (o == null) {
                    return false;
                }
                if (!(o instanceof OverrideEquals)) {
                    return false;
                }
                if (o == this) {
                    return true;
                }
                if ((o.getData() == this.data) && (o.getName().equals(name)) {
                    return true;
                }
            }
        }
10. Polymorphism, Dynamic Binding
    * Write some code for parents class and all the child classes can take advantage of it
    ````Java
    public interface animal { //all methods in interfaces are public and abstract
        //any instance data in a interface is static and final
        void eat();
        void swim();
        void sleep();
        //all classes that implement this interface must override all of these methods
    }
    ````

    * ### Code for next few points
        ````Java
        public interface Aquatic {
            public void swim();
        }

        public abstract class Fish implements Aquatic {
            public void swim() { print("Fish's Swim") };
            public void eat() { print("Fish's Eat") };
        }

        public class Shark extends Fish {
            public void attack() { print("Shark's Attack") };
        }

        public class Mako extends Shark {
            public void attack() { print("Mako's Attack") };
        }

        public class Baracuda extends Fish {
            public void jump() { print("Baracuda's Jump") };
        }
    * Java determines at compile time if this will run or if this will work
        * Basics:
            * if the method you are trying to call is also present in the parent class of the object (or the static type of the object) then the compliler says its ok and it compiles. 
            * For example:
            ```Java
            Shark s1 = new Mako();
            s1.attack();
            ````
            * This will compile because there is an attack method in the Shark class, but at Runtime (dynamic binding) this is where JVM decides to use the Mako attack method since this is a Mako object, and "Mako's attack" will be printed to the console.
            * Remember Fish is an abstract class so you cant say
             ````Java 
            Aquatic a1 = new Fish();
            ```` 
            * because you cannot instantiate an abstract class
            * you cannot cast up
            ````Java
            Mako s1 = new Shark();
            ````
            * Because every Mako is a shark, but not every Shark is a Mako; this will result in a **compile error** (Cant cast up)
            * This is ok, even though Shark does not have a eat method, it extends Fish which does have an eat method
            ````Java
            Shark s2 = new Mako();
            s2.eat();
            ````
            * this will print "Fish's Eat"
            * This wont run cause Object does not have a method called jump
            ````Java
            Object o1 = new Shark();
            o1.eat();
            ````
            * This is what happens when you cast something
            ````Java
            Fish f2 = new Mako();
            ( (Shark) f2).attack();
            //this will print Mako's attack because no matter what you cast it too the object is still a Mako, the static type does not matter
            ````
            * Illegall explicit Casting
            ````Java
            Fish f1 = new Shark(); //this is legal
            ( (Baracuda) f1).swim(); //this is illegal because a Shark and a Baracuda are not related
            ````
11. Interfaces
    * Interfaces are abstract classes, but a little different
        * they cannot have instance data, and if they do it needs to be final and static
        * all their methods are abstract
        * think of it as a blueprint that all classes that implement this interface have to follow, and every class that implements this interface must override all the abstract methods in the interface
    * Comparable
        * Classes that implement Comparable (Integer, Double, String, Date, etc.) can be compared using a **compareTo** method (what we did in homeworks).
        * Classes that **DO NOT** implement Comparable can be compared by defining a **Comparator**
        * Components to defining a Comparator: Implement Comparator and Serializable (explained later). Create a **compare** method that compares whatever values you want.
        * Defining a Comparator:
        ````Java
        public class GeometricObject implements Comparator<Geometric Object>, java.io.Serializable {
            public int compare(GeometricObject g1, GeometricObject g2) {
                (Area methods that return 1 or -1 depending on if g1.area() > g2.area() )
            }
        }
        ````
        * **Serializable**: Generally a good idea for comparators to implement Serializable, as they may be used
        as ordering methods in serializable data structures. In order for the data structure to serialize
        successfully, the comparator (if provided) must implement Serializable.
        * Comparable Basics:
            - We can sort the elements of:
                1. String objects
                2. Wrapper class objects
                3. User-defined class objects
            - Basic Example
            ````Java
            class Student implements Comparable<Student>{  
                int rollno;  
                String name;  
                int age;  
                Student (int rollno,String name,int age) {  
                    this.rollno=rollno;  
                    this.name=name;  
                    this.age=age;  
                }

                public int compareTo(Student st) {  
                    if(age==st.age)  
                        return 0;  
                    else if(age>st.age)  
                        return 1;  
                    else  
                        return -1;  
                }  
            }
            ````
            ````Java
            import java.util.*;  
            import java.io.*;  

            public class TestSort3 {  
                public static void main(String args[]) {  
                    ArrayList<Student> al=new ArrayList<Student>();  
                    al.add(new Student(101,"Vijay",23));  
                    al.add(new Student(106,"Ajay",27));  
                    al.add(new Student(105,"Jai",21));  
            
                    Collections.sort(al);  
                    for(Student st:al){  
                        System.out.println(st.rollno+" "+st.name+" "+st.age);  
                    }  
                }  
            }
            ````
            * What is printed 
            ````Text
            105 Jai 21
            101 Vijay 23
            106 Ajay 27 
            ````
    * Iterator, Iterable
        * Collection extends the **Iterable Interface**
        * **All** Collections are **iterable**. Obtain its **Iterator Object** to traverse through the collection.
        * iterator() method returns an instance of Iterable
        * Making an iterator: `Iterator<String> iterator = collection.iterator();`
        * Use hasNext() and next() methods to get the next element
    
12. Asymptotics, Programming Efficiency
    * Sorting
        * Merge Sort - O(n log n)
        * Insertion Sort - O(n^2)
        * Quick Sort - O(n log n)
        * Selection Sort - O(n^2)
    * Searching
        * Binary Search - O(log n)
        * Linear Search - 0(n)
13. Exceptions & File I/O
    * Defining your own exceptions
        ````Java
        public class CustomException extends Exception {
            //this is a checked exception because it happens at Compile Time
            //you surround checked exceptions with a try...catch block becuse they need to be handled
            public CustomException() {
                super("Some Custom Message"); //this adds a custom message to your custom exception
                //you can also make a constructor with arguments so you can have a more specfific custom message, but the super constructor only takes in a string as an argument
            }
        }

        public class CustomUnCheckedException extends RuntimeException {
            //this is an unchecked exception
            //it usually happens at runtime and you cannot handle these type of exceptions
        }
        ````
        - if an exception occurs at a line of code, that code is still considered to execute
    * File I/O
        * `import java.io.*;`
        * This is how you define a new file
        ````Java
        String x = "path/to/file.txt";
        File file = new File(x);
        ````
        * common file commands
        ````Java
        file.exists(); //checks if the file exists or does not
        file.isDir(); //checks if the file is a directory or not
        ````
        * Reading from a file
        ````Java
        import java.util.Scanner;

        Scanner input = new Scanner(file);
        input.hasNextLine(); \\returns a Boolean, true or false
        String firstLine = input.nextLine(); //store the first line of the file into this variable
        String secondLine = input.nextLine(); //store the next line of the file into this variable
        ````
        * Writing to a File
        ````Java
        File output = new File("path/to/output");
        Printstream out = new Printstream(output); //creates a printstream object of your file type
        out.println(firstLine); //prints the first line from the original file into this new file, and ends it with a "\n"
        out.println(secondLine); //does the same for the second line
        ````
14. Recursion
    * **Direct Recursion:** When the method calls itself
    * **Indirect Recursion:** Method A invokes method B, which then invokes method A again.
    ````Java
    public static int factorial(int n) {
        return (n * factorial(n - 1);
    }
    ````
    * Negative Aspects of recursion: uses up too much time and too much memory.
    * Generally **less efficient** to use recursion for mathematical processes.
    * **Tail Recursion**: When there is nothing else to be executed after the last recursive call. Ex: Above factorial method **IS NOT** tail recursive because at      the very end, all the numbers must be multiplied. **MOST IDEAL**
    * Tail Recursive factorial method: 
    ````Java
    public class ComputeFactorialTailRecursion {
        public static long factorial(int n) {
            return factorial(n, 1);
        }
        /** Auxiliary tail-recursive method for factorial */
        private static long factorial(int n, int result) {
            if (n == 0) {
                return result;
            } else {
                return factorial(n - 1, n * result);
            }
        }
    }
    ````
15. GUIs - Java FX
    * Event Driven Programming
        * system is waiting in a loop for something to happen, when something happens it responds
        * How to write event handling code
    * Principles
    * Graphics
    * Controls 
        * Buttons
        * ScrollBars
        * TextViews
        * ...
    * Chapter 14
        - Replaced Swing and AWT
        - **Must** extend javafx.application.application and implement the `start(PrimaryStage stage)` method.
        - A stage is a window for displaying a scene. You can add nodes to a scene. Panes, controls,
        and shapes are nodes. Panes can be used as the containers for nodes.
        - **FlowPane** arranges the nodes in the pane horizontally from left to right or vertically
        from top to bottom in the order in which they were added.
        - **GridPane** arranges nodes in a grid (matrix) formation. The nodes are placed in the specified column and row indices.
        - **BorderPane** can place nodes in five regions: top, bottom, left, right, and center.
        - **HBox** lays out its children in a single horizontal row. 
        - **VBox** lays out its children in  a single vertical column.
        - **TextField** disply text and accept text input from the user
        - **Nodes** elements in the scene graph
        - HBox, VBox - use .getChildren().addAll(text, button, box, pane, etc) to add stuff to the item
        - Panes - use .set(), or .setCenter() -> for BorderPanes
    * Chapter 15
        - Root class of JavaFX event class: **javafx.event.Event**. Subclasses of Event deal with action events, window events, mouse events, key events.
        - The handler object’s class must implement the corresponding event-handler interface.
        JavaFX provides a handler interface EventHandler<T extends Event>. The handler interface contains the handle(T e) method for handling
        event e.
        - Handler object must be registered by the source object. Registration methods depend on the event type. For an action event, the method is setOnAction. For a mouse-pressed event, the method is setOnMousePressed. For a key-pressed event, the method is setOnKeyPressed.
        -  **Functional Interface**: interface that has exactly one abstract method. Also known as a Single Abstract Method (SAM) Interface.
        - 3 objects involved in handling an interface event: **EventHandler**, **UIControl** (textfield, button, etc), and **Event** (what you are doing to call an action
        - Lambdas can be used to simplify the event-handling code. Ex: 
        ````Java
        ballPane.setOnMouseReleased(e -> ballPane.play()); 
        ballPane.setOnKeyPressed(e -> {
            if (e.getCode() == KeyCode.UP) {
                ballPane.increaseSpeed();
            }
        });
        ````
        - ballPane - UIControl
        - setOneKeyPressed - Event
        - e - EventHandler
        * Chapter 16
            - Abstract Labeled class is the base class for Label, Button, CheckBox, and RadioButton. It defines properties alignment, contentDisplay, text, graphic, graphicTextGap, textFill, underline, and wrapText.
            - Abstract ButtonBase class is the base class for Button, CheckBox, and RadioButton. It defines the onAction property for specifying a handler for action events.
            - TextField fires an action event when clicking the Enter key with the text field
            focused. A TextArea is often used for editing a multiline text.
            - ComboBox<T> and ListView<T> are generic classes for storing elements of type T. The elements in a combo box or a list view are stored in an observable list.
    * Examples: 
        * Practice Problems - Two windows, text from one window is put on to the other window
        ````Java
        import javafx.application.Application;
        import javafx.scene.Scene;
        import javafx.scene.control.Button;
        import javafx.scene.control.Label;
        import javafx.scene.control.TextField;
        import javafx.scene.layout.HBox;
        import javafx.stage.Stage;


        public class TwoWindows extends Application {

            @Override
            public void start(Stage primaryStage) {

                TextField tf = new TextField(); //makes a new textfield
                Label label = new Label("Enter Text"); //makes a new label, takes a string constructor
                Button bt = new Button("Show"); //makes a new button, takes a string constructor
                HBox box = new HBox(); //makes a new Horizontal Box, used to organize elements in the scene
                box.getChildren().addAll(label, tf, bt); //the procedure to add elements to a Hbox (or even a VBox)

                HBox hbox2 = new HBox(); 

                bt.setOnAction(e -> { //this is the method for declaring EventHandlers, this is a lambda expression, it is basically saying that whenever the button is pressed run this method
                String sum = tf.getText(); //getting the text from the textfield
                Label label1 = new Label(sum); //making that text into a label
                hbox2.getChildren().add(label1); //adding that label to the second hbox
                });
                Scene sceneOne = new Scene(box, 500, 500); //setting up the scene, with a box and dimensions
                Stage secondaryStage = new Stage(); //Setting up another stage (another window)
                Scene sceneTwo = new Scene(hbox2, 500, 500); //setting up the second scene, with the second box and same dimensions
                primaryStage.setScene(sceneOne); //setting the scene in the first stage
                secondaryStage.setScene(sceneTwo); //doing the same for the secondaryStage
                primaryStage.show(); //showing the primaryStage, very important
                secondaryStage.show(); //same for the secodary stage

            }
        }
        ````
        * Practice Problems - Cursor in the left half makes the rectangle blue, the other half is red
        ````Java
        import javafx.application.Application;
        import javafx.scene.Scene;
        import javafx.scene.layout.Pane;
        import javafx.scene.paint.Color;
        import javafx.stage.Stage;
        import javafx.scene.shape.Rectangle;


        public class ChangeColor extends Application {

            @Override
            public void start(Stage primaryStage) {
                Pane pane = new Pane(); //making a new Pane, everything is added to the top left automatically
                Rectangle rect = new Rectangle(200, 200); //making a new rectangle

                pane.getChildren().add(rect); //adding the rectangle to the pane

                Scene scene = new Scene(pane); //adding the pane to the scene

                primaryStage.setScene(scene); //adding scene to the stage
                primaryStage.show(); //showing the stage

                rect.setOnMouseMoved (event -> { //whenever the mouse moves over the rectangle call this
                    if (event.getX() < rect.getWidth()/2) { //if this position of the mouse is on the left half of the rectangle
                        rect.setFill(Color.BLUE); //set the color to blue
                    } else {
                        rect.setFill(Color.RED); //otherwise set it to red
                    }
                });
            }
        }
        ````

16. Inner Classes & Lambdas
    * Inner Classes**
        - a class defined within the scope of another class, useful for defining handler classes
        - compiled as *OuterClassName*$*InnerClassName*.class
        - can reference data and methods defined in the outer class
        - a **static** inner class cannot access **nonstatic** members of the outer class
        - Can be used in class other than the outer class it nests in
        - Example:
        ````Java
        public void start(Stage primaryStage) {
            btEnlarge.setOnAction(new EnlargeHandler());
        } 
        class EnlargeHandler implements EventHandler<ActionEvent> {
            public void handle(ActionEvent e) {
            circlePane.enlarge();
            }
        }
        ````
    * Anonymous Inner Class
        - must always extend a superclass or implement an interface, but cannot have an explicit extends or implements clause
        - must implement all abstract methods of superclass
        - No need to explicitly state **class**
        - Example
        ````Java
        public void start(Stage primaryStage) {
            btEnlarge.setOnAction( EventHandler<ActionEvent>() {
                public void handle(ActionEvent e) {
                circlePane.enlarge();
                }
            });
        }
        ````
        - The syntax for an anonymous inner class is shown below
        ````Java
            new SuperClassName/InterfaceName() {
            // Implement or override methods in superclass or interface
            // Other methods if necessary
            }
        ````
    * Lambdas   
        - simplified anonymous class
        - compiler treats Lambda expression as Object, instance of **EventHandler<ActionEvent>**
        - A functional interface is the interface with exactly one method. A lambda expression works only with a functional interface
        ````Java
        btn.setOnAction(e -> {
            System.out.println("ActionEvent is optional");
        });
        ````
        - The data type for a parameter may be explicitly declared or implicitly inferred by the compiler.
        - The parentheses can be omitted if there is only one parameter without an explicit data
        type.
17. Data Structures
    * Collections
        - One container to store a collection of elements is called a collection
        - Storing key/value pairs is called a map
    * Iterable
        - each collection is iterable
        - An iterator is a special class that allows a user to traverse a data structure
        - They typically have three methods:
            1. Get the current item
            2. Go to next item
            3. Go to previous item
        - The data structure typically implements its own iterator, as an inner/ private class
        - In Java, each data structure will implement the `java.lang.Iterator` interface.
        - The data structure would also implement the `java.lang.Iterable` interface, which has one method `iterable()`, that returns a new iterator object
        - `java.lang.Iterator` methods
            * **hasNext():** Returns a boolean representing whether there is another item in the structure
            * **next():** Returns the next item in the structure
            * **remove():** An optional method that returns the most recently returned element
        - `java.lang.Iterable` methods
            * **iterator():** returns a new iterator object
        - Instead of directly using the iterator object, Java lets us use a for each loop.
            - Java implicitly uses the iterator for the data structure, returning items as the iterator defines
        - Example Code:
        ````Java
        public static main(String[] args) {
            Collection<String> collection = new ArrayList<>();
            //add stuff to the collection
            Iterator<String> iterator = collection.iterator();
            while (iterator.hasNext()) {
                System.out.println(iterator.next());
            }
        }
        ````
        - other data structures have their own iterator, like ListIterator for Lists
    * Comparator
        - If the class does not implement comparable, meaning you cannot call compareTo on it you have to define your own comparable class
        - for example here is a comparable class for an abritary gemoetry class
        ````Java
        public class GeometricObjectComparator implements Comparator<GeometricObject>, java.io.Serializable {
            public int compare(GeometricObject g1, GeometricObject g2) {
                double area1 = g1.getArea();
                double area2 = g2.getArea();

                if (area1 < area2) {
                    return -1;
                }
                else if (area1 == area2) {
                    return 0;
                }
                else {
                    return 1;
                }
            }
        }
        ````
        - you implement Serializable because this may be used to order objects in data structures
    * Abstract Data Types
        * An Abstract Data Type is two things:
            * First pick a data type
            * Then, what are the operations you can do with this data type
                * For example, ints need to be able to be added together, subtracted, etc. 
        * Abstract Data Type: 
            - An abstract data type represents a model of a data structure which specifies basic characteristics of data and the operations which can be performed on it. 
            - For instance, in Java the List interface is a good example. This is an interface and it's not some particular implementation. It defines what data it deals with (a collection of something) and a set of operations like add(), addAll(), clear() etc. 
            - The examples of particular implementations are ArrayList, LinkedList, Stack etc. By implementing the List interface these classes become "Lists" themselves.
        * Logical Data Structure
    * Real Data Structures
        * Sets (Set Abstract Data Type)
            - Set is an Abstract Data Type that represents an unordered collection of elements
            - These are nonduplicate elements
                - so when you want to add something to this it is O(n), because you have to check for duplicates
            - Examples of sets are:
                1. HashSet
                2. TreeSet
                3. LinkedHashSet
                4. EnumSet
        * Lists
            1. Singly Linked List
                - FIFO - first in first out (for remove() method (no arg))
                - Ordered Singly Linked List
                    - Add(Item) - O(1)
                    - Remove(Item) - O(n) have to go through the list
            2. Doubly Linked List
        * Stacks
            - store objects processed in a last in, first out fashion
            - The Stack class was introduced prior to Java 2. The methods shown in Figure 20.11 were
            used before Java 2. The empty() method is the same as isEmpty(). 
            - The peek() method looks at the element at the top of the stack without removing it. 
            - The pop() method removes the top element from the stack and returns it. 
            - The push(Object element) method adds the specified element to the stack. 
            - The search(Object element) method checks whether the specified element is in the stack.
        * Queues
            - store objects processed in a first in, firs out fashion
            - The offer method is used to add an element to the queue. This method is similar to the
            add method in the Collection interface, but the offer method is preferred for queues.
            The poll and remove methods are similar, except that poll() returns null if the queue is
            empty, whereas remove() throws an exception. The peek and element methods are similar,
            except that peek() returns null if the queue is empty, whereas element() throws an
            exception.
        * PriorityQueue
            - store objects that are processed in the order of their priorities
            - In a priority queue, elements are assigned
            priorities. When accessing elements, the element with the highest priority is removed first.
        * LinkedHashMap - unordered map (it puts the keys in the order you give it, and changes the values)
        	- This default behavior only happens when you call the no-args constructor of the LinkedHashMap
            - This is sort of like a dictionary, it extends HashMap
            - It provides a sort of Link however, so you can iterate over the order they were added to the list
            - The order you insert the Nodes is the order you iterate through them
        * TreeMap - can take in a LinkedHashMap and reorder it so it is ordered by keys, not by the order that you put them in
            - All of the maps can take in a map argument in the constructor and it will make the associating Data Structure based on this map
        * Collections
            - Collections in java are a single unit of objects
            - This framework provides many interfaces (Set, List, Queue, Deque etc.)
            - And classes (ArrayList, Vector, LinkedList, PriorityQueue, HashSet, LinkedHashSet, TreeSet etc.)
            - All the operations that you perform on a data such as searching, sorting, insertion, manipulation, deletion etc. can be performed by Java Collections
            - Basically collections represents a set of classes and interfaces that all data structures inherit or extend from
            - Collections framework provide the Blueprint/Artictecure to store and manipulate data
            
18. Hashing
   * Every object has a method, `public int hashchode()`
   * Basic HashMap idea
    - passed in some key and some value
    - find hascode of key
    - mod key with size of array
    - this is the index
    - check if the current index is null, if it is not null keep adding 1 to index (make sure to mod with the size of the array so you dont go over)
    - keep checking until you find a null spot, if the Map is full expand it
    - add the Bucket to the empty index
    - Done!
   * Hashing is just making sure that each unique object has some sort of unique identifier.
   * **Load Factor**
    - The load factor is just how much you want to the Array to hold before you expand it
    - High load factor means more collisions (table is fuller). Collisions require searching for open spots (extra work) on additions, more checks to find right items on retrievals or removals. That extra work translates into being slower.
   * Usually this means that you want to make sure every object has some sort of integer to refer to it (usually a 32-bit integer)
   * Most hashing functions use linear probing to resolve conflicts, increases the index by one each time (this causes clusters)
   * Quadratic Probing also used
    - you do (n+1)^2 + index to get the new index, if that new index has a conflict also then you do (n+2)^2 + index
   * **HASHMAP**
   	- For example lets say you have a table of 11 elements, and you want to put a key of '1' in there
	- | Index        | Key          |
		| ------------- |:-------------:| 
		| 0     |  | 
		| 1    | 1 |
		| 2 |  |
		| 3 |  |
		| 4 |  |
		| 5 |  |
		| 6 |  |
		| 7 |  |
		| 8 |  |
		| 9 |  |
		| 10 |  |
	- Now you want to add the key of 45 here, since 45 is bigger than 11 we need to use modular arithmetic
		- 45 % 11 = 1
		- ERROR: Index 1 is already taken, so in linear probing it would just keep adding 1 until it finds an open spot, in this case 2, and would put the key in 2
		- However, in a **Double Hashing Function** another function is used to resolve collisions
	- In this particular example the secondary hashing function is h(k) = 7 - k % 7
		- h(45) = 7 - (45 % 7) = 7 - 3 = 4
		- Add 4 to the index of collision, 1, get a new index of 5. This is where 45 is placed
	- | Index        | Key          |
		| ------------- |:-------------:| 
		| 0     |  | 
		| 1     | 1 |
		| 2 |  |
		| 3 |  |
		| 4 |  |
		| 5 | 45 |
		| 6 |  |
		| 7 |  |
		| 8 |  |
		| 9 |  |
		| 10 |  |

## Pragmatics
1. Exam should be around 16 questions
2. Should take around 2 hours
3. 1/3 from the stuff after the last exam
    1. JavaFX
    2. Data Structures
    3. Inner Clases & Lambdas
4. 2/3 Cummulative from Exam 1-3s

## Examples
1. Adding elements to a Singly_Linked List With Keys, these keep the Keys in order
	i . Answer from Google Docs:
	````Java
	Public void add(Object key, Object elt) {
		Node newNode = new Node(elt);
		Node nextNode = this.head;
		While (nextNode.next != null && newNode.key < nextNode.key) {
			nextNode = nextNode.next;
		}
		Node temp = nextNode.next;
		nextNode.next = newNode;
		newNode.next = temp;
		//add fringe case for when it’s placed at the tail
	}
	````

````Java
public class SinglyLinkedMethods<E> {
    private Node<E> head;
    private int counter;

    public SinglyLinkedMethods() {
        
    }
    
    public static void main(String[] args) {
        Element a = new Element(1, "A");
        Element b = new Element (8, "B");
        Element c = new Element(3, "C");
        Element d = new Element(10, "D");
        
        SinglyLinkedMethods<String> list = new SinglyLinkedMethods<>();
        list.add(b);
        list.add(c);
        list.add(d);
        list.add(a);
        list.print();
    }
    
    public void add(Element elt) {
        int count = 0;
        Node<E> add = new Node(elt);
        Node current = head;
        
        if (current == null) {
            add.setNext(null);
            head = add;
            return;
        }
        if (current.getNext() == null) {
            if (current.getElement().getKey() < add.getElement().getKey()) {
                current.setNext(add);
                add.setNext(null);
                return;
            } else {
                add.setNext(current);
                head = add;
                return;
            }
        }
        if (current.getElement().getKey() > add.getElement().getKey()) {
            add.setNext(current);
            head = add;
            return;
        }
        while ((current.getNext() != null) && (current.getNext().getElement().getKey() < add.getElement().getKey())) {
            current = current.getNext();
            count++;
        }
        Node temp = current.getNext();
        current.setNext(add);
        add.setNext(temp);
    }
    
    public void print() {
        Node current = head;
        while (current.getNext() != null) {
            System.out.println(current.getElement().getData());
            current = current.getNext();
        }
        System.out.println(current.getElement().getData());
    }
    
    public String getHead() {
        return this.head.getElement().getData();
    }
}

class Node<U> {
    private Node next;
    private Element element;
    
    public Node() {
        this.next = null;
        this.element = null;
    }
    
    public Node(Element elt) {
        this.next = null;
        this.element = elt;
    }
    
    public Node(Element elt, Node n) {
        this.element = elt;
        this.next = n;
    }
    
    public Element getElement() {
        return this.element;
    }
    
    public Node<U> getNext() {
        return this.next;
    }
    
    public void setNext(Node<U> node) {
        this.next = node;
    }
    
}

class Element {
    private int key;
    private String data;
    
    public Element(int k, String dat) {
        this.key = k;
        this.data = dat;
    }
    
    public int getKey() {
        return this.key;
    }
    
    public String getData() {
        return this.data;
    }
}
````
