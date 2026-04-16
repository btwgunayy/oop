# ooppublic class Book {
    private String title;
    private double price;
    
    // Two-parameter constructor
    public Book(String title, double price) {
        this.title = title;
        setPrice(price); // Using setter to validate
    }
    
    // Getter methods
    public String getTitle() {
        return title;
    }
    
    public double getPrice() {
        return price;
    }
    
    // Setter with validation
    public void setPrice(double price) {
        if (price > 0) {
            this.price = price;
        } else {
            System.out.println("Error: Price must be positive");
        }
    }
    
    // Print info method
    public void printInfo() {
        System.out.printf("Title: %s, Price: %.2f\n", title, price);
    }
    
    public static void main(String[] args) {
        System.out.println("=== Book Class Test ===\n");
        
        // Create Book object
        Book book = new Book("Java Basics", 29.99);
        
        System.out.println("Initial book info:");
        book.printInfo();
        
        System.out.println("\nTesting setPrice() with invalid value (-15.00):");
        book.setPrice(-15.00);
        
        System.out.println("\nTesting setPrice() with valid value (45.50):");
        book.setPrice(45.50);
        
        System.out.println("\nFinal book info:");
        book.printInfo();
        
        System.out.println("\nUsing getters:");
        System.out.println("Title: " + book.getTitle());
        System.out.println("Price: $" + book.getPrice());
    }
}
