import java.util.Scanner;

enum MachineState {
    BUY,
    FILL,
    TAKE,
    REMAINING,
    NEUTRAL,
    EXIT;

}

public class CoffeeMachine {

    private int waterAvailable = 400;
    private int milkAvailable = 540;
    private int coffeeAvailable = 120;
    private int disposableCups = 9;
    private int currentTakings = 550;
    private boolean machineOn = false;
    private static Scanner scanner = new Scanner(System.in);

    public static void main(String[] args) {

        CoffeeMachine machine = new CoffeeMachine();
        machine.machineOn = true;

        while (machine.machineOn) {
            machine.machineStart(machine);
        }

    }


    public void machineStart(CoffeeMachine machine) {
        System.out.println("Write action (buy, fill, take, remaining, exit):");
        machineInteract(scanner.next() , machine);
    }

    public static void machineInteract(String uInput, CoffeeMachine machine) {
        MachineState currentState = MachineState.valueOf(uInput.toUpperCase());

        while (machine.machineOn) {
            switch (currentState) {
                case BUY:
                    System.out.println("What do you want to buy? 1 - espresso, 2 - latte, 3 - cappuccino, back - to main menu:");
                    String buyChoice = scanner.next();

                    if (buyChoice.toLowerCase().contains("back")) {
                        currentState = MachineState.NEUTRAL;
                        break;
                    } else {
                        int choice = Integer.parseInt(buyChoice);
                        if (choice == 1 || choice == 2 || choice == 3) {
                            machine.buy(choice);
                            currentState = MachineState.NEUTRAL;
                            break;
                        } else {
                            currentState = MachineState.NEUTRAL;
                            break;
                        }
                    }
                case FILL:
                    machine.fill();
                    currentState = MachineState.NEUTRAL;
                    break;

                case TAKE:
                    machine.take();
                    currentState = MachineState.NEUTRAL;
                    break;

                case REMAINING:
                    machine.machineUpdate();
                    currentState = MachineState.NEUTRAL;
                    break;

                case EXIT:
                    machine.machineOn = false;
                    currentState = MachineState.NEUTRAL;
                    break;

                case NEUTRAL:
                    machine.machineStart(machine);
                    break;

                default:
                    System.out.println("Unknown choice try again");

            }
        }
    }

    public void buy(int choice) {

        boolean outOfResources = isOutOfResources(choice);

        if (!outOfResources) {
            System.out.println("I have enough resources, making you a coffee!");
            switch (choice) {
                case 1:
                    waterAvailable = waterAvailable - 250;
                    coffeeAvailable = coffeeAvailable - 16;
                    currentTakings = currentTakings + 4;
                    disposableCups--;
                    break;

                case 2:
                    waterAvailable = waterAvailable - 350;
                    milkAvailable = milkAvailable - 75;
                    coffeeAvailable = coffeeAvailable - 20;
                    currentTakings = currentTakings + 7;
                    disposableCups--;
                    break;

                case 3:
                    waterAvailable = waterAvailable - 200;
                    milkAvailable = milkAvailable - 100;
                    coffeeAvailable = coffeeAvailable - 12;
                    currentTakings = currentTakings + 6;
                    disposableCups--;
                    break;
            }
        }
    }


    public boolean isOutOfResources(int choice) {
        boolean noResources = false;
        if (disposableCups == 0) {
            System.out.println("Sorry no cups");
            noResources = true;
        } else {
            switch (choice) {
                case 1:
                    if (waterAvailable < 250) {
                        System.out.println("Sorry, not enough water!");
                        noResources = true;
                        break;
                    }
                    if (coffeeAvailable < 16) {
                        System.out.println("Sorry, not enough coffee!");
                        noResources = true;
                        break;
                    }
                    break;

                case 2:
                    if (waterAvailable < 350) {
                        System.out.println("Sorry, not enough water!");
                        noResources = true;
                        break;
                    }
                    if (milkAvailable < 75) {
                        System.out.println("Sorry, not enough milk!");
                        noResources = true;
                        break;
                    }
                    if (coffeeAvailable < 20) {
                        System.out.println("Sorry, not enough coffee!");
                        noResources = true;
                        break;
                    }
                    break;

                case 3:
                    if (waterAvailable < 200) {
                        System.out.println("Sorry, not enough water!");
                        noResources = true;
                        break;
                    }
                    if (milkAvailable < 100) {
                        System.out.println("Sorry, not enough milk!");
                        noResources = true;
                        break;
                    }
                    if (coffeeAvailable < 12) {
                        System.out.println("Sorry, not enough coffee!");
                        noResources = true;
                        break;
                    }
                    break;

                default:
                    System.out.println("Unknown choice");
                    noResources = true;
            }
        }
        return noResources;
    }


    public void fill() {
        System.out.println("Write how many ml of water do you want to add: ");
        waterAvailable += scanner.nextInt();

        System.out.println("Write how many ml of milk do you want to add:");
        milkAvailable += scanner.nextInt();

        System.out.println("Write how many grams of coffee beans do you want to add:");
        coffeeAvailable += scanner.nextInt();

        System.out.println("Write how many disposable cups of coffee do you want to add:");
        disposableCups += scanner.nextInt();
    }

    public void machineUpdate() {
        System.out.println("The coffee machine has:");
        System.out.println(waterAvailable + " of water");
        System.out.println(milkAvailable + " of milk");
        System.out.println(coffeeAvailable + " of coffee beans");
        System.out.println(disposableCups + " of disposable cups");
        System.out.println(currentTakings + " of money");
    }



    public void take() {
        System.out.println("I gave you $" + currentTakings);
        System.out.println();
        currentTakings = 0;
    }




}
