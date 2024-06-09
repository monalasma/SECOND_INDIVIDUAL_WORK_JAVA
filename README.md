# SECOND_INDIVIDUAL_WORK_JAVA
Making a book ArrayList
MAIN class:
```java
import java.util.Scanner;
import java.util.ArrayList;
public class Main{
  public static BookManager bookManager = new           BookManager();
  public static void main(String[] args) {
   while (true){
      Scanner scanner = new Scanner (System.in);
     System.out.println("Press 1 to add a book.");
     System.out.println("Press 2 to remove a book.");
     var userInput = scanner.nextLine();
     if (userInput.equals("1")){
       addBook();
     }else if(userInput.equals("2")){
       removeBook();
       break;
     }else{
       break;
     }
   }
  }
  public static void addBook(){
    Scanner scanner = new Scanner(System.in);
    System.out.println("Welcome to your Book list. Please enter the Author of the book: ");
    var Author = scanner.nextLine();
    System.out.println("Please enter the Title of the book: ");
    var Title = scanner.nextLine();
    //scanner.close();
    var Book = new Book (Author, Title);
    bookManager.addBook(Book);
  }
  public static void removeBook(){
    Scanner scanner = new Scanner(System.in);
    System.out.println("Please enter the Title of the book you want to remove or write 'quit': ");
    String input = scanner.nextLine();
    if (input.equalsIgnoreCase("quit")) {
        System.out.println("You entered quit, here is your book collection: ");
        for (Book book : bookManager.getBookCollection()) {
            System.out.println("- " + book.getTitle());
        }
    } else{
      System.out.println("The book you want to remove is " + "'" + input + "'" + ". The book is removed from your book list.");
        bookManager.remove(input);
      } 
    }
  }
```
BOOK class:
```java
public class Book{
  public String Author;
  public String Title; 
  

  public Book(String Author, String Title){
    this.Author = Author;
    this.Title = Title;
  }
  public String getTitle(){
    return Title;
  }
}
```
BOOKMANAGER class:
```java
import java.util.ArrayList;

public class BookManager{
  public ArrayList<Book> bookCollection = new ArrayList<>();

  public void addBook(Book book){
    bookCollection.add(book);
  }
  public ArrayList<Book> getBookCollection(){
    return bookCollection;
  }
  public void remove(String bookToRemove) {
    bookCollection.removeIf(book -> book.getTitle().equalsIgnoreCase(bookToRemove));
  }
}
```


