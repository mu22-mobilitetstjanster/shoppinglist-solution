# shoppinglist-solution

Main.java
```java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class Main {

  public static void main(String[] args) {

    //Skapa ett program som läser in produkter i en matlista tills att användaren skriver "done".
    // Malistan får max innehålla 10 produkter.

    // Ifall användaren skriver in fler än 10 produkter ska programmet
    // fråga vilken vara användaren vill ersätta den nya varan med


    List<String> shoppingList = createShoppingList();

    System.out.println("Now go and buy following products!");
    for (int i = 0; i < shoppingList.size(); i++) {
      System.out.println((i + 1) + " - " + shoppingList.get(i));
    }

  }

  public static void addItem(String item, List<String> shoppingList) {
    if(shoppingList.size() == 5) {
      System.out.println("List is full, which item do you wish to replace? ");
      String oldItem = askForItem();

      int oldItemIndex = shoppingList.indexOf(oldItem); // ger index, eller -1 om elementet inte fanns
      if(oldItemIndex != -1) { //hittad vara!
        // ersätta vara
        shoppingList.set(oldItemIndex, item);
      }
    } else {
      shoppingList.add(item);
    }
    System.out.println(shoppingList);
  }

  // 1. Fråga användaren om en vara
  public static String askForItem() {
    Scanner scanner = new Scanner(System.in);
    System.out.println("Write item: ");
    String response = scanner.nextLine();

    return response;
  }


  public static List<String> createShoppingList() {
    List<String> shoppingList = new ArrayList<>();
    boolean isDone = false;
    String item = "";

    // 2. Fråga 1. tills att användaren skriver "done"
    while(!isDone) { //"done", "DONE", "DoNE" ...
      item = askForItem();

      if(item.equalsIgnoreCase("done")) {
        isDone = true;
      } else {
        addItem(item, shoppingList);
      }
    }

    return shoppingList;
  }

}

```
