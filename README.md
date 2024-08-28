# LIBRARY-MANAGEMENT
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class LibraryManagementSystem {
    private List<Book> bookList;

    public LibraryManagementSystem() {
        bookList = new ArrayList<>();
    }

    public void addBook(Book book) {
        bookList.add(book);
        System.out.println("Book added successfully!");
    }

    public void removeBook(String title) {
        for (Book book : bookList) {
            if (book.getTitle().equals(title)) {
                bookList.remove(book);
                System.out.println("Book removed successfully!");
                return;
            }
        }
        System.out.println("Book not found!");
    }

    public void searchBook(String title) {
        for (Book book : bookList) {
            if (book.getTitle().equals(title)) {
                System.out.println("Book found!");
                System.out.println("Title: " + book.getTitle());
                System.out.println("Author: " + book.getAuthor());
                System.out.println("Year: " + book.getYear());
                return;
            }
        }
        System.out.println("Book not found!");
    }

    public static void main(String[] args) {
        LibraryManagementSystem library = new LibraryManagementSystem();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("1. Add book");
            System.out.println("2. Remove book");
            System.out.println("3. Search book");
            System.out.println("4. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();

            switch (option) {
                case 1:
                    System.out.print("Enter book title: ");
                    String title = scanner.next();
                    System.out.print("Enter book author: ");
                    String author = scanner.next();
                    System.out.print("Enter book year: ");
                    int year = scanner.nextInt();
                    Book book = new Book(title, author, year);
                    library.addBook(book);
                    break;
                case 2:
                    System.out.print("Enter book title to remove: ");
                    String removeTitle = scanner.next();
                    library.removeBook(removeTitle);
                    break;
                case 3:
                    System.out.print("Enter book title to search: ");
                    String searchTitle = scanner.next();
                    library.searchBook(searchTitle);
                    break;
                case 4:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid option!");
            }
        }
    }
}

class Book {
    private String title;
    private String author;
    private int year;

    public Book(String title, String author, int year) {
        this.title = title;
        this.author = author;
        this.year = year;
    }

    public String getTitle() {
        return title;
    }

    public String getAuthor() {
        return author;
    }

    public int getYear() {
        return year;
    }
}
