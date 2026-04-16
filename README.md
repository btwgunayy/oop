import java.util.Arrays;

// ==================== QUESTION 1: BOOK CLASS ====================
class Book {
    private String title;
    private double price;
    
    public Book(String title, double price) {
        this.title = title;
        setPrice(price);
    }
    
    public String getTitle() { return title; }
    public double getPrice() { return price; }
    
    public void setPrice(double price) {
        if (price > 0) this.price = price;
        else System.out.println("Error: Price must be positive");
    }
    
    public void printInfo() {
        System.out.printf("Title: %s, Price: %.2f\n", title, price);
    }
}

// ==================== QUESTION 2: PERSON CLASS ====================
class PersonClass {
    private String name;
    private int age;
    
    public PersonClass(String name, int age) {
        this.name = name;
        setAge(age);
    }
    
    public String getName() { return name; }
    public int getAge() { return age; }
    
    public void setAge(int age) {
        if (age >= 0 && age <= 150) this.age = age;
        else System.out.println("Error: Age is not valid");
    }
    
    public void printInfo() {
        System.out.printf("Name: %s, Age: %d\n", name, age);
    }
}

// ==================== QUESTION 3: PRODUCT CLASS ====================
class Product {
    private String productName;
    private int stock;
    
    public Product(String productName, int stock) {
        this.productName = productName;
        setStock(stock);
    }
    
    public String getProductName() { return productName; }
    public int getStock() { return stock; }
    
    public void setStock(int stock) {
        if (stock >= 0) this.stock = stock;
        else System.out.println("Error: Stock cannot be negative");
    }
    
    public void addStock(int amount) {
        if (amount > 0) {
            stock += amount;
            System.out.println("Added " + amount + " units. New stock: " + stock);
        } else System.out.println("Error: Amount must be positive");
    }
    
    public void printInfo() {
        System.out.printf("Product: %s, Stock: %d\n", productName, stock);
    }
}

// ==================== QUESTION 4: TEMPERATURE CLASS ====================
class Temperature {
    private double celsius;
    
    public Temperature(double celsius) {
        setCelsius(celsius);
    }
    
    public double getCelsius() { return celsius; }
    
    public double toFahrenheit() {
        return celsius * 9/5 + 32;
    }
    
    public void setCelsius(double celsius) {
        if (celsius > -273.15) this.celsius = celsius;
        else System.out.println("Error: Temperature below absolute zero");
    }
    
    public void printInfo() {
        System.out.printf("Celsius: %.1f, Fahrenheit: %.1f\n", celsius, toFahrenheit());
    }
}

// ==================== QUESTION 5: CIRCLE CLASS ====================
class Circle {
    private double radius;
    
    public Circle() {
        this(1.0);
    }
    
    public Circle(double radius) {
        this.radius = radius;
    }
    
    public double area() {
        return Math.PI * radius * radius;
    }
    
    public double circumference() {
        return 2 * Math.PI * radius;
    }
    
    public void printInfo() {
        System.out.printf("Radius: %.1f, Area: %.2f, Circumference: %.2f\n", 
                         radius, area(), circumference());
    }
}

// ==================== QUESTION 6: BOX CLASS ====================
class Box {
    private double length, width, height;
    
    public Box() {
        this(1.0, 1.0, 1.0);
    }
    
    public Box(double side) {
        this(side, side, side);
    }
    
    public Box(double length, double width, double height) {
        this.length = length;
        this.width = width;
        this.height = height;
    }
    
    public double volume() {
        return length * width * height;
    }
    
    public double surfaceArea() {
        return 2 * (length*width + width*height + height*length);
    }
    
    public void printInfo() {
        System.out.printf("Box (%.1f x %.1f x %.1f) - Volume: %.2f, Area: %.2f\n",
                         length, width, height, volume(), surfaceArea());
    }
}

// ==================== QUESTION 7: MATHHELPER CLASS ====================
class MathHelper {
    public static int max(int a, int b) { return (a > b) ? a : b; }
    public static double max(double a, double b) { return (a > b) ? a : b; }
    public static int max(int a, int b, int c) { return max(max(a, b), c); }
    public static int min(int a, int b) { return (a < b) ? a : b; }
    public static double min(double a, double b) { return (a < b) ? a : b; }
    public static double average(double a, double b, double c) { return (a + b + c) / 3; }
}

// ==================== QUESTION 8: PRINTER CLASS ====================
class Printer {
    public void print(int value) { System.out.println("Integer: " + value); }
    public void print(double value) { System.out.println("Double: " + value); }
    public void print(String value) { System.out.println("String: " + value); }
    public void print(boolean value) { System.out.println("Boolean: " + value); }
    public void print(int value, int times) {
        for (int i = 0; i < times; i++) System.out.println("Integer: " + value);
    }
}

// ==================== QUESTION 9: ANIMAL & DOG ====================
class Animal {
    protected String name;
    protected String sound;
    
    public Animal(String name, String sound) {
        this.name = name;
        this.sound = sound;
    }
    
    public void makeSound() {
        System.out.println(name + " says " + sound);
    }
}

class Dog extends Animal {
    private String breed;
    
    public Dog(String name, String sound, String breed) {
        super(name, sound);
        this.breed = breed;
    }
    
    @Override
    public void makeSound() {
        super.makeSound();
        System.out.println("Breed: " + breed);
    }
    
    public void fetch() {
        System.out.println(name + " is fetching the ball!");
    }
}

// ==================== QUESTION 10: ACCOUNT & SAVINGSACCOUNT ====================
class Account {
    protected String owner;
    protected double balance;
    
    public Account(String owner, double balance) {
        this.owner = owner;
        this.balance = balance;
    }
    
    public void deposit(double amount) {
        balance += amount;
        System.out.println("Deposited: $" + amount);
    }
    
    public void printInfo() {
        System.out.printf("Owner: %s, Balance: $%.2f\n", owner, balance);
    }
}

class SavingsAccount extends Account {
    private double interestRate;
    
    public SavingsAccount(String owner, double balance, double interestRate) {
        super(owner, balance);
        this.interestRate = interestRate;
    }
    
    public void applyInterest() {
        double interest = balance * interestRate;
        balance += interest;
        System.out.printf("Interest applied: $%.2f (Rate: %.2f%%)\n", interest, interestRate * 100);
    }
    
    @Override
    public void printInfo() {
        super.printInfo();
        System.out.printf("Interest Rate: %.2f%%\n", interestRate * 100);
    }
}

// ==================== QUESTION 11: PERSON, STUDENT, TEACHER ====================
class Person {
    protected String name;
    protected int age;
    
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
    
    public void introduce() {
        System.out.printf("Hi, I am %s and I am %d years old.\n", name, age);
    }
}

class Student extends Person {
    private String major;
    
    public Student(String name, int age, String major) {
        super(name, age);
        this.major = major;
    }
    
    @Override
    public void introduce() {
        super.introduce();
        System.out.println("I study " + major + ".");
    }
}

class Teacher extends Person {
    private String subject;
    
    public Teacher(String name, int age, String subject) {
        super(name, age);
        this.subject = subject;
    }
    
    @Override
    public void introduce() {
        super.introduce();
        System.out.println("I teach " + subject + ".");
    }
}

// ==================== QUESTION 12: PHONE & SMARTPHONE ====================
class Phone {
    protected String brand;
    protected String model;
    
    public Phone(String brand, String model) {
        this.brand = brand;
        this.model = model;
    }
    
    public void call(String number) {
        System.out.println("Calling " + number + "...");
    }
    
    public void printInfo() {
        System.out.printf("Brand: %s, Model: %s\n", brand, model);
    }
}

class SmartPhone extends Phone {
    private String osVersion;
    
    public SmartPhone(String brand, String model, String osVersion) {
        super(brand, model);
        this.osVersion = osVersion;
    }
    
    public void installApp(String appName) {
        System.out.println("Installing " + appName + " on " + brand + " " + model);
    }
    
    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("OS Version: " + osVersion);
    }
}

// ==================== QUESTION 13: VEHICLE HIERARCHY ====================
abstract class Vehicle {
    protected String type;
    
    public Vehicle(String type) {
        this.type = type;
    }
    
    public abstract double fuelCost();
    
    public void printVehicle() {
        System.out.printf("Vehicle: %s, Fuel Cost per km: $%.2f\n", type, fuelCost());
    }
}

class Car extends Vehicle {
    private double mileage;
    
    public Car(String type, double mileage) {
        super(type);
        this.mileage = mileage;
    }
    
    @Override
    public double fuelCost() {
        return 1.0 / mileage;
    }
}

class Truck extends Vehicle {
    private double payload;
    
    public Truck(String type, double payload) {
        super(type);
        this.payload = payload;
    }
    
    @Override
    public double fuelCost() {
        return 0.05 * payload;
    }
}

// ==================== QUESTION 14: INSTRUMENT HIERARCHY ====================
abstract class Instrument {
    protected String name;
    
    public Instrument(String name) {
        this.name = name;
    }
    
    public abstract void play();
    
    public void describe() {
        System.out.println("Instrument: " + name);
    }
}

class Guitar extends Instrument {
    private int strings;
    
    public Guitar(String name, int strings) {
        super(name);
        this.strings = strings;
    }
    
    @Override
    public void play() {
        System.out.println(name + " goes Strum Strum! (" + strings + " strings)");
    }
}

class Piano extends Instrument {
    private int keys;
    
    public Piano(String name, int keys) {
        super(name);
        this.keys = keys;
    }
    
    @Override
    public void play() {
        System.out.println(name + " goes Ding Dong! (" + keys + " keys)");
    }
}

// ==================== QUESTION 15: EMPLOYEE HIERARCHY ====================
abstract class Employee {
    protected String name;
    protected double hoursWorked;
    
    public Employee(String name, double hoursWorked) {
        this.name = name;
        this.hoursWorked = hoursWorked;
    }
    
    public abstract double calculatePay();
    
    public void printPayslip() {
        System.out.printf("Employee: %s, Pay: $%.2f\n", name, calculatePay());
    }
}

class FullTimeEmployee extends Employee {
    private double monthlySalary;
    
    public FullTimeEmployee(String name, double hoursWorked, double monthlySalary) {
        super(name, hoursWorked);
        this.monthlySalary = monthlySalary;
    }
    
    @Override
    public double calculatePay() {
        return monthlySalary;
    }
}

class PartTimeEmployee extends Employee {
    private double hourlyRate;
    
    public PartTimeEmployee(String name, double hoursWorked, double hourlyRate) {
        super(name, hoursWorked);
        this.hourlyRate = hourlyRate;
    }
    
    @Override
    public double calculatePay() {
        return hoursWorked * hourlyRate;
    }
}

// ==================== QUESTION 16: FOOD HIERARCHY ====================
abstract class Food {
    protected String name;
    protected int calories;
    
    public Food(String name, int calories) {
        this.name = name;
        this.calories = calories;
    }
    
    public abstract String getCategory();
    
    public void printFood() {
        System.out.printf("Food: %s, Calories: %d, Category: %s\n", name, calories, getCategory());
    }
}

class Fruit extends Food {
    public Fruit(String name, int calories) {
        super(name, calories);
    }
    
    @Override
    public String getCategory() {
        return "Fruit";
    }
}

class FastFood extends Food {
    private boolean extraFat;
    
    public FastFood(String name, int calories, boolean extraFat) {
        super(name, calories);
        this.extraFat = extraFat;
    }
    
    @Override
    public String getCategory() {
        return extraFat ? "Fast Food (High Fat)" : "Fast Food";
    }
}

// ==================== QUESTION 17: LIBRARY BOOK ====================
class LibraryBook {
    private String title;
    private String author;
    private boolean isAvailable;
    
    public LibraryBook() {
        this.title = "Unknown";
        this.author = "Unknown";
        this.isAvailable = true;
    }
    
    public LibraryBook(String title, String author) {
        this.title = title;
        this.author = author;
        this.isAvailable = true;
    }
    
    public void checkout() {
        if (isAvailable) {
            isAvailable = false;
            System.out.println(title + " has been checked out.");
        } else {
            System.out.println("Error: Book is not available.");
        }
    }
    
    public void returnBook() {
        isAvailable = true;
        System.out.println(title + " has been returned.");
    }
    
    public void printInfo() {
        System.out.printf("Title: %s, Author: %s, Available: %b\n", title, author, isAvailable);
    }
}

// ==================== QUESTION 18: SCOREBOARD ====================
class Scoreboard {
    private String playerName;
    private int score;
    
    public Scoreboard() {
        this.playerName = "Player";
        this.score = 0;
    }
    
    public Scoreboard(String playerName) {
        this.playerName = playerName;
        this.score = 0;
    }
    
    public void addPoints(int points) {
        if (points > 0) {
            score += points;
            System.out.println("Added " + points + " points. New score: " + score);
        } else {
            System.out.println("Error: Points must be positive.");
        }
    }
    
    public void deductPoints(int points) {
        if (points > 0 && (score - points) >= 0) {
            score -= points;
            System.out.println("Deducted " + points + " points. New score: " + score);
        } else if (points <= 0) {
            System.out.println("Error: Invalid deduction. Points must be positive.");
        } else {
            System.out.println("Error: Invalid deduction. Score would go below 0.");
        }
    }
    
    public void resetScore() {
        score = 0;
        System.out.println("Score has been reset to 0.");
    }
    
    public void printScore() {
        System.out.printf("Player: %s, Score: %d\n", playerName, score);
    }
}

// ==================== QUESTION 19: STAFF & SUPERVISOR ====================
class Staff {
    private String name;
    private double hourlyRate;
    
    public Staff(String name, double hourlyRate) {
        this.name = name;
        this.hourlyRate = hourlyRate;
    }
    
    public String getName() { return name; }
    public double getHourlyRate() { return hourlyRate; }
    
    public double calculateWeeklyPay(int hours) {
        return hourlyRate * hours;
    }
    
    public void printInfo() {
        System.out.printf("Staff: %s, Rate: $%.2f/hr\n", name, hourlyRate);
    }
}

class Supervisor extends Staff {
    private int teamSize;
    
    public Supervisor(String name, double hourlyRate, int teamSize) {
        super(name, hourlyRate);
        this.teamSize = teamSize;
    }
    
    @Override
    public double calculateWeeklyPay(int hours) {
        return super.calculateWeeklyPay(hours) + (50.0 * teamSize);
    }
    
    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("Team Size: " + teamSize);
    }
}

// ==================== QUESTION 20: NOTIFICATION SYSTEM ====================
abstract class Notification {
    protected String recipient;
    
    public Notification(String recipient) {
        this.recipient = recipient;
    }
    
    public abstract void send();
    
    public void log() {
        System.out.println("[Notification sent to: " + recipient + "]");
    }
}

class EmailNotification extends Notification {
    private String subject;
    
    public EmailNotification(String recipient, String subject) {
        super(recipient);
        this.subject = subject;
    }
    
    @Override
    public void send() {
        System.out.printf("Email to %s: Subject: %s\n", recipient, subject);
    }
}

class SMSNotification extends Notification {
    private String phoneNumber;
    
    public SMSNotification(String recipient, String phoneNumber) {
        super(recipient);
        this.phoneNumber = phoneNumber;
    }
    
    @Override
    public void send() {
        System.out.printf("SMS to %s for %s\n", phoneNumber, recipient);
    }
}

class PushNotification extends Notification {
    private String appName;
    
    public PushNotification(String recipient, String appName) {
        super(recipient);
        this.appName = appName;
    }
    
    @Override
    public void send() {
        System.out.printf("Push from %s to %s\n", appName, recipient);
    }
}

// ==================== QUESTION 21: COUNTER ====================
class Counter {
    private int count;
    
    public Counter() {
        this.count = 0;
    }
    
    public void increment() {
        count++;
        System.out.println("Incremented to: " + count);
    }
    
    public void decrement() {
        if (count > 0) {
            count--;
            System.out.println("Decremented to: " + count);
        } else {
            System.out.println("Error: Counter cannot go below zero.");
        }
    }
    
    public void reset() {
        count = 0;
        System.out.println("Counter reset to: 0");
    }
    
    public void setCount(int value) {
        if (value >= 0) {
            count = value;
            System.out.println("Count set to: " + count);
        } else {
            System.out.println("Error: Count cannot be negative.");
        }
    }
    
    public int getCount() {
        return count;
    }
}

// ==================== QUESTION 22: TRIANGLE ====================
class Triangle {
    private double a, b, c;
    
    public Triangle(double side) {
        this(side, side, side);
    }
    
    public Triangle(double base, double height) {
        this(base, height, height);
    }
    
    public Triangle(double a, double b, double c) {
        this.a = a;
        this.b = b;
        this.c = c;
    }
    
    public double perimeter() {
        return a + b + c;
    }
    
    public boolean isEquilateral() {
        return a == b && b == c;
    }
    
    public void printInfo() {
        System.out.printf("Sides: %.2f, %.2f, %.2f | Perimeter: %.2f | Equilateral: %b\n",
                         a, b, c, perimeter(), isEquilateral());
    }
}

// ==================== QUESTION 23: SHAPE & COLOREDSHAPE ====================
class Shape {
    protected int sides;
    
    public Shape(int sides) {
        this.sides = sides;
    }
    
    public int getSides() { return sides; }
    
    public void describe() {
        System.out.println("This shape has " + sides + " sides.");
    }
    
    public boolean isPolygon() {
        return sides >= 3;
    }
}

class ColoredShape extends Shape {
    private String color;
    
    public ColoredShape(int sides, String color) {
        super(sides);
        this.color = color;
    }
    
    @Override
    public void describe() {
        super.describe();
        System.out.println("Color: " + color + ".");
    }
}

// ==================== QUESTION 24: PAYMENT SYSTEM ====================
abstract class Payment {
    protected double amount;
    
    public Payment(double amount) {
        this.amount = amount;
    }
    
    public abstract void processPayment();
    
    public void printReceipt() {
        System.out.printf("Payment of $%.2f processed.\n", amount);
    }
}

class CreditCardPayment extends Payment {
    private String cardLastFour;
    
    public CreditCardPayment(double amount, String cardLastFour) {
        super(amount);
        this.cardLastFour = cardLastFour;
    }
    
    @Override
    public void processPayment() {
        System.out.printf("Credit card ending in %s charged $%.2f.\n", cardLastFour, amount);
    }
}

class CashPayment extends Payment {
    private double cashGiven;
    
    public CashPayment(double amount, double cashGiven) {
        super(amount);
        this.cashGiven = cashGiven;
    }
    
    @Override
    public void processPayment() {
        if (cashGiven >= amount) {
            System.out.printf("Cash received: $%.2f, Change: $%.2f\n", cashGiven, cashGiven - amount);
        } else {
            System.out.printf("Error: Insufficient cash. Need $%.2f more.\n", amount - cashGiven);
        }
    }
}

// ==================== QUESTION 25: CONVERTER ====================
class Converter {
    public double convert(double km) {
        return km * 0.621371;
    }
    
    public double convert(int feet) {
        return feet * 0.3048;
    }
    
    public double convert(double celsius, String unit) {
        if (unit.equals("F")) return celsius * 9/5 + 32;
        else if (unit.equals("K")) return celsius + 273.15;
        else return 0;
    }
    
    public void printResult(String from, double input, String to, double output) {
        System.out.printf("%.2f %s = %.2f %s\n", input, from, output, to);
    }
}

// ==================== QUESTION 26: MEDIA HIERARCHY ====================
class Media {
    protected String title;
    protected int year;
    
    public Media(String title, int year) {
        this.title = title;
        this.year = year;
    }
    
    public void play() {
        System.out.printf("Playing: %s (%d)\n", title, year);
    }
    
    public void printInfo() {
        System.out.printf("Title: %s, Year: %d\n", title, year);
    }
}

class Movie extends Media {
    private String director;
    
    public Movie(String title, int year, String director) {
        super(title, year);
        this.director = director;
    }
    
    @Override
    public void printInfo() {
        super.printInfo();
        System.out.println("Director: " + director);
    }
}

class Podcast extends Media {
    private String host;
    private int episodeCount;
    
    public Podcast(String title, int year, String host, int episodeCount) {
        super(title, year);
        this.host = host;
        this.episodeCount = episodeCount;
    }
    
    @Override
    public void play() {
        System.out.printf("Playing: %s (%d) - Host: %s, Episodes: %d\n", title, year, host, episodeCount);
    }
    
    @Override
    public void printInfo() {
        System.out.printf("Title: %s, Year: %d, Host: %s, Episodes: %d\n", title, year, host, episodeCount);
    }
}

// ==================== QUESTION 27: SUBSCRIPTION PLANS ====================
abstract class Subscription {
    private String userName;
    
    public Subscription(String userName) {
        this.userName = userName;
    }
    
    public String getUserName() { return userName; }
    public abstract double monthlyFee();
    
    public void printPlan() {
        System.out.printf("User: %s, Monthly Fee: $%.2f\n", userName, monthlyFee());
    }
}

class BasicPlan extends Subscription {
    public BasicPlan(String userName) {
        super(userName);
    }
    
    @Override
    public double monthlyFee() {
        return 9.99;
    }
}

class PremiumPlan extends Subscription {
    private int extraFeatures;
    
    public PremiumPlan(String userName, int extraFeatures) {
        super(userName);
        this.extraFeatures = extraFeatures;
    }
    
    @Override
    public double monthlyFee() {
        return 9.99 + 4.99 * extraFeatures;
    }
}

class FamilyPlan extends Subscription {
    private int members;
    
    public FamilyPlan(String userName, int members) {
        super(userName);
        this.members = members;
    }
    
    @Override
    public double monthlyFee() {
        return 14.99 + 2.99 * members;
    }
}

// ==================== QUESTION 28: INVENTORY ITEM ====================
class InventoryItem {
    private String itemName;
    private int quantity;
    private double unitPrice;
    
    public InventoryItem(String itemName, int quantity, double unitPrice) {
        this.itemName = itemName;
        this.quantity = quantity;
        this.unitPrice = unitPrice;
    }
    
    public String getItemName() { return itemName; }
    public int getQuantity() { return quantity; }
    public double getUnitPrice() { return unitPrice; }
    
    public void sell(int amount) {
        if (amount > quantity) {
            System.out.println("Error: Not enough stock. Available: " + quantity);
        } else {
            quantity -= amount;
            System.out.println("Sold " + amount + " " + itemName + "(s). Remaining: " + quantity);
        }
    }
    
    public void restock(int amount) {
        if (amount > 0) {
            quantity += amount;
            System.out.println("Restocked " + amount + " " + itemName + "(s). New quantity: " + quantity);
        } else {
            System.out.println("Error: Restock amount must be positive.");
        }
    }
    
    public double totalValue() {
        return quantity * unitPrice;
    }
    
    public void printInfo() {
        System.out.printf("Item: %s, Qty: %d, Price: $%.2f, Total: $%.2f\n", 
                         itemName, quantity, unitPrice, totalValue());
    }
}

// ==================== QUESTION 29: GAME CHARACTER ====================
class GameCharacter {
    protected String name;
    protected int health;
    
    public GameCharacter(String name, int health) {
        this.name = name;
        this.health = Math.max(0, health);
    }
    
    public void takeDamage(int amount) {
        health = Math.max(0, health - amount);
        System.out.println(name + " took " + amount + " damage! HP: " + health);
    }
    
    public void heal(int amount) {
        health += amount;
        System.out.println(name + " healed " + amount + " HP! HP: " + health);
    }
    
    public void attack() {
        System.out.println(name + " attacks!");
    }
    
    public void printStatus() {
        System.out.printf("Character: %s, HP: %d\n", name, health);
    }
}

class Warrior extends GameCharacter {
    private int armor;
    
    public Warrior(String name, int health, int armor) {
        super(name, health);
        this.armor = armor;
    }
    
    @Override
    public void takeDamage(int amount) {
        int reducedDamage = Math.max(0, amount - armor);
        health = Math.max(0, health - reducedDamage);
        System.out.printf("%s took %d damage (reduced by armor %d)! HP: %d\n", 
                         name, reducedDamage, armor, health);
    }
    
    @Override
    public void attack() {
        System.out.println(name + " swings a sword for extra damage!");
    }
}

class Mage extends GameCharacter {
    private int mana;
    
    public Mage(String name, int health, int mana) {
        super(name, health);
        this.mana = mana;
    }
    
    public void castSpell() {
        if (mana >= 20) {
            mana -= 20;
            System.out.println(name + " casts a spell! Mana: " + mana);
        } else {
            System.out.println("Not enough mana! Need 20 mana, have " + mana);
        }
    }
    
    @Override
    public void attack() {
        castSpell();
    }
}

// ==================== QUESTION 30: TRANSPORT SYSTEM ====================
abstract class Transport {
    protected String origin;
    protected String destination;
    
    public Transport(String origin, String destination) {
        this.origin = origin;
        this.destination = destination;
    }
    
    public abstract double ticketPrice();
    public abstract int travelTime();
    
    public void printTrip() {
        System.out.printf("From %s to %s | Price: $%.2f | Time: %d min\n", 
                         origin, destination, ticketPrice(), travelTime());
    }
}

class Bus extends Transport {
    private double distanceKm;
    
    public Bus(String origin, String destination, double distanceKm) {
        super(origin, destination);
        this.distanceKm = distanceKm;
    }
    
    @Override
    public double ticketPrice() {
        return 0.10 * distanceKm;
    }
    
    @Override
    public int travelTime() {
        return (int)(distanceKm * 1.5);
    }
}

class Train extends Transport {
    private double distanceKm;
    
    public Train(String origin, String destination, double distanceKm) {
        super(origin, destination);
        this.distanceKm = distanceKm;
    }
    
    @Override
    public double ticketPrice() {
        return 0.15 * distanceKm;
    }
    
    @Override
    public int travelTime() {
        return (int)(distanceKm * 0.8);
    }
}

class Plane extends Transport {
    private int flightDuration;
    
    public Plane(String origin, String destination, int flightDuration) {
        super(origin, destination);
        this.flightDuration = flightDuration;
    }
    
    @Override
    public double ticketPrice() {
        return 50.0 + flightDuration * 2;
    }
    
    @Override
    public int travelTime() {
        return flightDuration;
    }
}

// ==================== MAIN CLASS - TEST HAMISINI ====================
public class CompleteAll {
    public static void main(String[] args) {
        System.out.println("==================== COMPLETE SOLUTION - ALL 30 QUESTIONS ====================\n");
        
        // Q1: Book
        System.out.println("========== Q1: BOOK ==========");
        Book book = new Book("Java Basics", 29.99);
        book.printInfo();
        book.setPrice(-15.00);
        book.setPrice(45.50);
        book.printInfo();
        
        // Q2: Person
        System.out.println("\n========== Q2: PERSON ==========");
        PersonClass person = new PersonClass("Sara", 25);
        person.printInfo();
        person.setAge(-5);
        person.setAge(30);
        person.printInfo();
        
        // Q3: Product
        System.out.println("\n========== Q3: PRODUCT ==========");
        Product product = new Product("Pen", 50);
        product.printInfo();
        product.addStock(25);
        product.setStock(100);
        product.printInfo();
        
        // Q4: Temperature
        System.out.println("\n========== Q4: TEMPERATURE ==========");
        Temperature temp = new Temperature(25.0);
        temp.setCelsius(-300.0);
        temp.setCelsius(100.0);
        temp.printInfo();
        
        // Q5: Circle
        System.out.println("\n========== Q5: CIRCLE ==========");
        new Circle().printInfo();
        new Circle(5.0).printInfo();
        
        // Q6: Box
        System.out.println("\n========== Q6: BOX ==========");
        new Box().printInfo();
        new Box(3.0).printInfo();
        new Box(2.0, 3.0, 4.0).printInfo();
        
        // Q7: MathHelper
        System.out.println("\n========== Q7: MATHHELPER ==========");
        System.out.println("max(10,20)=" + MathHelper.max(10,20) + ", max(15.5,12.3)=" + MathHelper.max(15.5,12.3));
        System.out.println("max(5,12,8)=" + MathHelper.max(5,12,8) + ", average(10,20,30)=" + MathHelper.average(10,20,30));
        
        // Q8: Printer
        System.out.println("\n========== Q8: PRINTER ==========");
        Printer printer = new Printer();
        printer.print(42);
        printer.print(3.14);
        printer.print("Hello");
        printer.print(true);
        printer.print(5, 3);
        
        // Q9: Animal & Dog
        System.out.println("\n========== Q9: ANIMAL & DOG ==========");
        new Animal("Generic", "Sound").makeSound();
        Dog dog = new Dog("Buddy", "Woof", "Golden");
        dog.makeSound();
        dog.fetch();
        
        // Q10: Account & Savings
        System.out.println("\n========== Q10: ACCOUNT & SAVINGS ==========");
        Account acc = new Account("John", 1000);
        acc.printInfo();
        SavingsAccount sav = new SavingsAccount("Jane", 2000, 0.05);
        sav.printInfo();
        sav.applyInterest();
        sav.printInfo();
        
        // Q11: Person, Student, Teacher
        System.out.println("\n========== Q11: PERSON, STUDENT, TEACHER ==========");
        new Person("Alice", 30).introduce();
        new Student("Bob", 20, "CS").introduce();
        new Teacher("Dr. Carol", 45, "Math").introduce();
        
        // Q12: Phone & Smartphone
        System.out.println("\n========== Q12: PHONE & SMARTPHONE ==========");
        Phone phone = new Phone("Nokia", "3310");
        phone.printInfo();
        phone.call("123456");
        SmartPhone sp = new SmartPhone("Apple", "iPhone15", "iOS17");
        sp.printInfo();
        sp.installApp("WhatsApp");
        
        // Q13: Vehicle Hierarchy
        System.out.println("\n========== Q13: VEHICLE ==========");
        Vehicle[] vehicles = {new Car("Sedan", 15), new Truck("Truck", 5)};
        for(Vehicle v : vehicles) v.printVehicle();
        
        // Q14: Instrument Hierarchy
        System.out.println("\n========== Q14: INSTRUMENT ==========");
        Instrument[] instruments = {new Guitar("Guitar", 6), new Piano("Piano", 88)};
        for(Instrument i : instruments) { i.describe(); i.play(); }
        
        // Q15: Employee Hierarchy
        System.out.println("\n========== Q15: EMPLOYEE ==========");
