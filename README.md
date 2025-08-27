# isat-subtask2
#include <iostream>
#include <string>
#include <bitset>
#include <cstdlib>  // for rand()
#include <ctime>    // for seeding rand()

using namespace std;

// Function 1: Decimal to Binary
string decimalToBinary(int number) {
    return bitset<16>(number).to_string().erase(0, bitset<16>(number).to_string().find('1'));
}

// Function 2: Binary to Decimal
int binaryToDecimal(string binary) {
    return stoi(binary, nullptr, 2);
}

// Function 3: Decimal to Hexadecimal
string decimalToHex(int number) {
    char buffer[20];
    sprintf(buffer, "%X", number);
    return string(buffer);
}

// Function 4: Hexadecimal to Decimal
int hexToDecimal(string hexStr) {
    return stoi(hexStr, nullptr, 16);
}

// Menu Display
void displayMenu() {
    cout << "\n===== Conversion Menu =====" << endl;
    cout << "1. Convert Decimal to Binary" << endl;
    cout << "2. Convert Binary to Decimal" << endl;
    cout << "3. Convert Decimal to Hexadecimal" << endl;
    cout << "4. Convert Hexadecimal to Decimal" << endl;
    cout << "5. Demo (Generate random number -> Binary)" << endl;
    cout << "6. Exit" << endl;
    cout << "Enter your choice (1-6): ";
}

int main() {
    srand(time(0)); // seed random generator
    int choice;

    do {
        displayMenu();
        cin >> choice;

        if (choice == 1) {
            int num;
            cout << "Enter decimal number: ";
            cin >> num;
            cout << "Binary: " << decimalToBinary(num) << endl;

        } else if (choice == 2) {
            string bin;
            cout << "Enter binary number: ";
            cin >> bin;
            cout << "Decimal: " << binaryToDecimal(bin) << endl;

        } else if (choice == 3) {
            int num;
            cout << "Enter decimal number: ";
            cin >> num;
            cout << "Hexadecimal: " << decimalToHex(num) << endl;

        } else if (choice == 4) {
            string hex;
            cout << "Enter hexadecimal number: ";
            cin >> hex;
            cout << "Decimal: " << hexToDecimal(hex) << endl;

        } else if (choice == 5) {
            int randNum = rand() % 100;
            cout << "Generated number: " << randNum << endl;
            cout << "Binary: " << decimalToBinary(randNum) << endl;

        } else if (choice == 6) {
            cout << "Exiting program..." << endl;

        } else {
            cout << "Invalid choice, please try again." << endl;
        }

    } while (choice != 6);

    return 0;
}
