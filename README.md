# JAVAWEEKPROJECT
CAMPUCONNECTION

shooping cart

import java.util.*;

// Product class
class Product {
    String name;
    int price;

    Product(String name, int price) {
        this.name = name;
        this.price = price;
    }
}

public class ShoppingCart {

    public static void main(String[] args) {

        Scanner sc = new Scanner(System.in);

        // ArrayList to store products
        ArrayList<Product> cart = new ArrayList<>();

        while (true) {
            System.out.println("\n1. Add Product");
            System.out.println("2. View Cart");
            System.out.println("3. Remove Product");
            System.out.println("4. Total Price");
            System.out.println("5. Exit");

            System.out.print("Enter choice: ");
            int choice = sc.nextInt();

            switch (choice) {

                case 1:
                    System.out.print("Enter product name: ");
                    String name = sc.next();

                    System.out.print("Enter price: ");
                    int price = sc.nextInt();

                    cart.add(new Product(name, price));
                    System.out.println("Product added!");
                    break;

                case 2:
                    if (cart.isEmpty()) {
                        System.out.println("Cart is empty!");
                    } else {
                        System.out.println("Products in Cart:");
                        for (Product p : cart) {
                            System.out.println(p.name + " - Rs." + p.price);
                        }
                    }
                    break;

                case 3:
                    System.out.print("Enter product name to remove: ");
                    String removeName = sc.next();

                    boolean found = false;

                    for (int i = 0; i < cart.size(); i++) {
                        if (cart.get(i).name.equals(removeName)) {
                            cart.remove(i);
                            found = true;
                            System.out.println("Product removed!");
                            break;
                        }
                    }

                    if (!found) {
                        System.out.println("Product not found!");
                    }
                    break;

                case 4:
                    int total = 0;
                    for (Product p : cart) {
                        total += p.price;
                    }
                    System.out.println("Total Price: Rs." + total);
                    break;

                case 5:
                    System.out.println("Thank you!");
                    return;

                default:
                    System.out.println("Invalid choice!");
            }
        }
    }
}
