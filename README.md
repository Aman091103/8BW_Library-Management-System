# 8BW_Library-Management-System
import java.util.*;

class Book {
    String title;
    String author;
    int bookId;

    public Book(int bookId, String title, String author) {
        this.bookId = bookId;
        this.title = title;
        this.author = author;
    }
}

class User {
    String username;
    int userId;

    public User(int userId, String username) {
        this.userId = userId;
        this.username = username;
    }
}

public class libararyManagementSystem {
    private ArrayList<Book> books;
    private ArrayList<User> users;
    private int bookIdCounter = 1;
    private int userIdCounter = 1;

    public libararyManagementSystem() {
        this.books = new ArrayList<>();
        this.users = new ArrayList<>();
    }

    public void addBook(String title, String author) {
        Book book = new Book(bookIdCounter++, title, author);
        books.add(book);
        System.out.println("Book added successfully: " + book.title);
    }

    public void deleteBook(int bookId) {
        for (Book book : books) {
            if (book.bookId == bookId) {
                books.remove(book);
                System.out.println("Book deleted successfully: " + book.title);
                return;
            }
        }
        System.out.println("Book not found with ID: " + bookId);
    }

    public void addUser(String username) {
        User user = new User(userIdCounter++, username);
        users.add(user);
        System.out.println("User added successfully: " + user.username);
    }

    public static void main(String[] args) {
        libararyManagementSystem librarySystem = new libararyManagementSystem();
        Scanner scanner = new Scanner(System.in);

        while (true) {
            System.out.println("\nLibrary Management System");
            System.out.println("1. Add Book");
            System.out.println("2. Delete Book");
            System.out.println("3. Add User");
            System.out.println("4. Exit");
            System.out.print("Enter your choice: ");

            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    System.out.print("Enter Book Title: ");
                    String title = scanner.next();
                    System.out.print("Enter Author Name: ");
                    String author = scanner.next();
                    librarySystem.addBook(title, author);
                    break;

                case 2:
                    System.out.print("Enter Book ID to delete: ");
                    int bookId = scanner.nextInt();
                    librarySystem.deleteBook(bookId);
                    break;

                case 3:
                    System.out.print("Enter User Name: ");
                    String username = scanner.next();
                    librarySystem.addUser(username);
                    break;

                case 4:
                    System.out.println("Exiting Library Management System. Goodbye!");
                    System.exit(0);

                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }
    }
}
