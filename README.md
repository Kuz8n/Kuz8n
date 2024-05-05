#include <iostream>
#include <iomanip>

using namespace std;

int main()
{
    const string itemNames[] = {
        "C2", "COKE", "SPRITE", "ROYAL", "MAGNOLIA", "MOUNTAIN DEW", "7UP", "PEPSI", 
        "STING", "COBRA", "SPARKLE", "WILKINS MINERAL", "MINUTE MAID", "LEMON JUICE", 
        "TANDUAY SELECT", "RED HORSE", "THE BAR", "GMS", "FUNDADOR"
    };
    const int itemPrices[] = {
        15, 20, 20, 20, 15, 25, 15, 25, 20, 20, 18, 20, 15, 15, 120, 120, 110, 110, 450
    };

    struct Item {
        string name;
        int price;
        int quantity;
    };

    Item selectedItems[20]; // To store selected items and quantities
    int selectedItemCount = 0;

    int subtotal = 0, total = 0;
    char choice;

    cout << fixed << setprecision(2); // Set precision for displaying currency

    cout << "List Of Items";
    cout << "\n Drinks & Liquor \n   |Number|";
    cout << "\n 1. C2                      15 ";
    cout << "\n 2. COKE                    20 ";
    cout << "\n 3. SPRITE                  20 ";
    cout << "\n 4. ROYAL				    20 ";
    cout << "\n 5. MAGNOLIA          	    15 ";
    cout << "\n 6. MOUNTAIN DEW	  	    25 ";
    cout << "\n 7. 7UP						15";
    cout << "\n 8. PEPSI					25";
    cout << "\n 9. STING					20";
    cout << "\n 10.COBRA					20";
    cout << "\n 11.SPARKLE					18";
    cout << "\n 12.WILKINS MINERAL			20";
    cout << "\n 13.MINUTE MAID				15";
    cout << "\n 14.LEMON JUICE 			15";
    cout << "\n 15.TANDUAY SELECT			120";
    cout << "\n 16.RED HORSE				120";
    cout << "\n 17.THE BAR					110";
    cout << "\n 18.GMS						110";
    cout << "\n 19.FUNDADOR				450";

    cout << "\n**********************************************" << endl;

    do {
        cout << "\nEnter Item Number: ";
        cin >> selectedItems[selectedItemCount].name;

        int item;
        try {
            item = stoi(selectedItems[selectedItemCount].name);
        } catch (const invalid_argument &e) {
            cout << "Invalid item entered!" << endl;
            return 1;
        }

        if (item < 1 || item > 19) {
            cout << "Invalid item entered!" << endl;
            return 1;
        }

        cout << "Enter Quantity: ";
        cin >> selectedItems[selectedItemCount].quantity;

        int itemPrice = itemPrices[item - 1];
        selectedItems[selectedItemCount].price = itemPrice;
        subtotal += itemPrice * selectedItems[selectedItemCount].quantity;

        selectedItemCount++;

        cout << "Do you want to add another item? (y/n): ";
        cin >> choice;

    } while (choice == 'y' || choice == 'Y');

    // Display selected items and quantities
    cout << "\nItems Selected:\n";
    for (int i = 0; i < selectedItemCount; ++i) {
        cout << "Item: " << itemNames[stoi(selectedItems[i].name) - 1] << " | Quantity: " << selectedItems[i].quantity << endl;
    }

    cout << "\nSubtotal: PHP" << subtotal << endl;

    // Total is same as subtotal, as we're not adding tax
    total = subtotal;
    cout << "Total: PHP" << total << endl;

    return 0;
}
