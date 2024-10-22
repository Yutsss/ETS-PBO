# ETS-PBO

**Nama** : Adyuta Prajahita Murdianto

**NRP** : 5025221186

**Kelas** : PBO A

---

## **1. Jelaskan perbedaan antara kelas dan objek, serta berikan contoh kode sederhana yang menunjukan hubungan kelas dan objek.**

`Kelas` adalah blueprint atau cetak biru yang menggambarkan atribut dan perilaku (method) apa saja dari suatu object yang akan dibuat, sedangkan `Objek` adalah instance atau realisasi dari suatu kelas. 

```java
public class Animal {
    public String name;

    public Animal(String name) {
        this.name = name;
    }

    public void makeSound() {
        System.out.println(name + " is making a sound.");
    }

    public void displayInfo() {
        System.out.println("Animal's name: " + name);
    }
}
```

```java
public class Main {
    public static void main(String[] args) {
        Animal myAnimal = new Animal("Dog");
        myAnimal.makeSound();
        myAnimal.displayInfo();
    }
}
```

Contoh diatas merupakan contoh dari kelas `Animal`, yang dimana memiliki atribut `nama`, serta method `kontruktor`, `makeSound`, dan `displayInfo`. `Objek` dari kelas ini akan dipanggil di `kelas` main dengan nilai parameter sebagai nama dari hewan yang akan di set di `konstruktor`. Lalu dipanggil method `makeSound` untuk mengeluarkan suara hewan, serta `displayInfo` untuk mencetak informasi dari objek hewan tersebut.

## **2. Buatlah aplikasi `CoffeeMachine` yang menyediakan kopi dengan harga tertentu.**

### **Kelas `Coffee`**

```java
public class Coffee {
    private String name;  
    private int price;     

    public Coffee(String name, int price) {
        this.name = name;
        this.price = price;
    }

    public String getName() {
        return name;
    }

    public int getPrice() {
        return price;
    }
}
```

Kelas yang merepresentasikan tiap kopi yang ada di `CoffeeMachine`. Setiap value atribut di set didalam method `kontruktor`, dan terdapat beberapa method `getter` untuk mendapatkan nilai dari masing-masing atribut. 

### **Kelas `CoffeeMachine`**

```java
public class CoffeeMachine {
    private ArrayList<Coffee> coffeeMenu;

    public CoffeeMachine() {
        this.coffeeMenu = new ArrayList<>();
    }

    public void addCoffee(String name, int price) {
        Coffee newCoffee = new Coffee(name, price);
        coffeeMenu.add(newCoffee);
    }

    public void displayMenu() {
        System.out.println("Available Coffee Menu:");
        for (int i = 0; i < coffeeMenu.size(); i++) {
            Coffee coffee = coffeeMenu.get(i);
            System.out.println(i + ". " + coffee.getName() + " - " + coffee.getPrice() + " units");
        }
    }

    public void buyCoffee(int index, int money) {
        if (index < 0 || index >= coffeeMenu.size()) {
            System.out.println("Invalid coffee selection.");
            return;
        }

        Coffee selectedCoffee = coffeeMenu.get(index);

        if (money >= selectedCoffee.getPrice()) {
            System.out.println("Serving " + selectedCoffee.getName() + ". Enjoy your coffee!");
        } else {
            System.out.println("Not enough money. " + selectedCoffee.getName() + " costs " + selectedCoffee.getPrice() + " units.");
        }
    }
}
```

Kelas yang merepresentasikan mesin kopi berfungsi sebagai kelas utama dari mesin kopi. Memiliki atribut `coffeeMenu` berupa array list yang berfungsi menyimpan objek-objek `Coffee`. Kelas `konstruktor` berfungsi untuk menginisiasi atribut `coffeeMenu` dengan array list kosong. Method `addCoffee` berfungsi untuk menambahkan kopi ke array `coffeeMenu`. Method `displayMenu` berfungsi untuk menampilkan seluruh kopi yang ada dialam array `coffeeMenu`. 
Terakhir, method `buyCoffee` berfungsi sebagai method untuk membeli kopi.