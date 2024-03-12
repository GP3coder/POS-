# POS-
//Here's an algorithm for a P.O.S system in C++:
#include <iostream>
#include <iomanip>
#include <map>

using namespace std;

// Define product prices
const map<int, double> productPrices = {
    {1, 1300.00},
    {2, 900.00},
    {3, 200.00},
    {4, 500.00},
    {5, 2500.00}
};

// Function to display product menu
void displayMenu() {
    cout << "GROUP 3 Product Menu:" << endl;
    cout << "1. Sure deodorant spray for men --- $1300.00" << endl;
    cout << "2. Rexona deodorant spray --------- $900.00" << endl;
    cout << "3. Canned Tiger beer -------------- $200.00" << endl;
    cout << "4. Maryland cookies --------------- $500.00" << endl;
    cout << "5. Hair closure ------------------- $2500.00" << endl;
}

int main() {
    int productCode;
    int quantity;
    double totalAmount = 0.0;
    map<int, int> cart;

    cout << "Welcome to GROUP 3 Store!" << endl;
    displayMenu();

    char choice;
    do {
        cout << "Enter product code (1-5): ";
        cin >> productCode;
        cout << "Enter quantity: ";
        cin >> quantity;

        if (productPrices.find(productCode) != productPrices.end()) {
            cart[productCode] += quantity;
            totalAmount += productPrices.at(productCode) * quantity;
        } else {
            cout << "Invalid product code. Please try again." << endl;
        }

        cout << "Do you want to add more items? (Y/N): ";
        cin >> choice;
    } while (toupper(choice) == 'Y');

    // Display receipt
    cout << "\n\nReceipt:" << endl;
    cout << "------------------------------------------" << endl;
    cout << setw(30) << left << "Product" << setw(10) << right << "Quantity" << setw(15) << right << "Amount" << endl;
    cout << "------------------------------------------" << endl;
    for (auto& item : cart) {
        cout << setw(30) << left << "Product " + to_string(item.first) << setw(10) << right << item.second << setw(15) << right << productPrices.at(item.first) * item.second << endl;
    }
    cout << "------------------------------------------" << endl;
    cout << setw(40) << left << "Total Amount: " << setw(15) << right << totalAmount << endl;
    cout << "------------------------------------------" << endl;

    return 0;
}
//This C++ program implements a P.O.S system for the GROUP 3 store. It allows users to select products by entering their respective codes and quantities. The program then calculates the total amount and displays a receipt showing the quantity of each item purchased and the total amount to be paid.
