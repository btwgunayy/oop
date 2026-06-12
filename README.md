import java.util.ArrayList;
import java.util.LinkedList;
import java.util.HashSet;
import java.util.HashMap;
import java.util.Iterator;

// ============================================================================
// 1. CLASSES, ENCAPSULATION & CONSTRUCTORS
// ============================================================================
class BankHesabi {
    private String sahib; // private -> Encapsulation
    private double balans;

    // Constructor
    public BankHesabi(String sahib, double ilkinBalans) {
        this.sahib = sahib;
        if (ilkinBalans >= 0) {
            this.balans = ilkinBalans;
        }
    }

    // Getter və Setter metodları
    public String getSahib() { return sahib; }
    public double getBalans() { return balans; }

    public void medaxilEt(double mebleg) {
        if (mebleg > 0) {
            this.balans += mebleg;
        }
    }
}

// ============================================================================
// 2. INHERITANCE & POLYMORPHISM
// ============================================================================
class Heyvan {
    public void sesChixar() {
        System.out.println("Heyvan naməlum səs çıxarır.");
    }
}

// Inheritance (Varislik)
class It extends Heyvan {
    // Polymorphism (Method Overriding)
    @Override
    public void sesChixar() {
        System.out.println("İt hürür: Hov-hov!");
    }
}

class Pishik extends Heyvan {
    @Override
    public void sesChixar() {
        System.out.println("Pişik miyovlayır: Miau!");
    }
}

// ============================================================================
// 3. PACKAGES & ACCESS CONTROL (Simulyasiya)
// ============================================================================
class Avtomobil {
    public String marka = "Toyota";       // Hər yerdən əlçatan
    private int maxSuret = 240;           // Yalnız bu sinif daxilində
    protected String reng = "Qara";       // Miras alanlar və eyni paket üçün

    public void suretiGoster() {
        // Private dəyişənə öz sinfində baxa bilirik
        System.out.println(marka + " maksimum sürəti: " + maxSuret + " km/saat");
    }
}

// ============================================================================
// MAIN CLASS - IntelliJ-də işləyəcək əsas hissə
// ============================================================================
public class Main {
    public static void main(String[] args) {

        System.out.println("=== 1. Classes & Encapsulation / Constructors ===");
        BankHesabi hesab = new BankHesabi("Anar", 500.0);
        hesab.medaxilEt(150.0);
        System.out.println("Hesab sahibi: " + hesab.getSahib());
        System.out.println("Son Balans: " + hesab.getBalans() + " AZN\n");


        System.out.println("=== 2. Inheritance & Polymorphism ===");
        Heyvan menimItim = new It();       // Polimorfizm yaradılır
        Heyvan menimPishiyim = new Pishik();

        menimItim.sesChixar();     // İt kimi davranır
        menimPishiyim.sesChixar(); // Pişik kimi davranır
        System.out.println();


        System.out.println("=== 3. Packages & Access Control ===");
        Avtomobil masin = new Avtomobil();
        System.out.println("Maşının markası (Public): " + masin.marka);
        // System.out.println(masin.maxSuret); -> XƏTA verər, çünki private-dır.
        masin.suretiGoster(); // Private dataya metod vasitəsilə dolayısı ilə baxırıq
        System.out.println();


        System.out.println("=== 4. Exception Handling ===");
        int[] massiv = {10, 20, 30};
        try {
            System.out.println("Massivin 5-ci elementi: " + massiv[5]); // Xəta nöqtəsi
        } catch (ArrayIndexOutOfBoundsException e) {
            System.out.println("Tutulan Xəta: Massiv indexi tapılmadı! -> " + e.getMessage());
        } finally {
            System.out.println("Finally bloku: Xəta olsa da, olmasa da işləyir.\n");
        }


        System.out.println("=== 5. ArrayList & LinkedList ===");
        // ArrayList nümunəsi
        ArrayList<String> telebeler = new ArrayList<>();
        telebeler.add("Əli");
        telebeler.add("Leyla");
        System.out.println("ArrayList (İlk tələbə): " + telebeler.get(0));

        // LinkedList nümunəsi
        LinkedList<String> novbe = new LinkedList<>();
        novbe.add("Aysel");
        novbe.addFirst("Rəşad"); // Əvvələ sürətli əlavə etmə
        System.out.println("LinkedList növbəsi: " + novbe + "\n");


        System.out.println("=== 6. HashMap, HashSet & Iterator ===");
        // HashSet (Dublikat qəbul etmir)
        HashSet<Integer> unikalEdedler = new HashSet<>();
        unikalEdedler.add(5);
        unikalEdedler.add(5); // Dublikat, əlavə olunmayacaq
        unikalEdedler.add(12);

        // Iterator istifadəsi
        Iterator<Integer> iterator = unikalEdedler.iterator();
        System.out.print("HashSet Elementləri (Iterator ilə): ");
        while(iterator.hasNext()) {
            System.out.print(iterator.next() + " ");
        }
        System.out.println();

        // HashMap (Key-Value)
        HashMap<String, String> sozluk = new HashMap<>();
        sozluk.put("Apple", "Alma");
        sozluk.put("Book", "Kitab");
        System.out.println("HashMap ('Apple' tərcüməsi): " + sozluk.get("Apple"));
        System.out.println("=============================================");
    }
}
