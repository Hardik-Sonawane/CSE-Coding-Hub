#include <iostream>
using namespace std;

void sortDescending(int costs[], int N) {
    for (int i = 0; i < N-1; ++i) {
        for (int j = i + 1; j < N; ++j) {
            if (costs[i] < costs[j]) {
                int temp = costs[i];
                costs[i] = costs[j];
                costs[j] = temp;
            }
        }
    }
}

int copyCostsLessThan500(const int costs[], int N, int newArray[]) {
    int index = 0;
    for (int i = 0; i < N; ++i) {
        if (costs[i] < 500) {
            newArray[index++] = costs[i];
        }
    }
    return index;
}

int removeDuplicatesUsingTempArray(int costs[], int N, int newArray[]) {
    bool seen[10000] = { false };
    int index = 0;
    for (int i = 0; i < N; ++i) {
        if (!seen[costs[i]]) {
            newArray[index++] = costs[i];
            seen[costs[i]] = true;
        }
    }
    return index;
}

int removeDuplicatesWithoutTempArray(int costs[], int N) {
    // Sort array
    for (int i = 0; i < N-1; ++i) {
        for (int j = i + 1; j < N; ++j) {
            if (costs[i] > costs[j]) {
                int temp = costs[i];
                costs[i] = costs[j];
                costs[j] = temp;
            }
        }
    }
    // Remove duplicates
    int newSize = 0;
    for (int i = 0; i < N; ++i) {
        if (i == 0 || costs[i] != costs[i - 1]) {
            costs[newSize++] = costs[i];
        }
    }
    return newSize;
}

int countBooksMoreThan500(const int costs[], int N) {
    int count = 0;
    for (int i = 0; i < N; ++i) {
        if (costs[i] > 500) {
            count++;
        }
    }
    return count;
}

void displayMenu() {
    cout << "Choose an operation:\n";
    cout << "1. Insert book costs\n";
    cout << "2. Sort costs in descending order\n";
    cout << "3. Display costs of books less than 500\n";
    cout << "4. Remove duplicates (using temp array) from costs less than 500\n";
    cout << "5. Remove duplicates (without temp array) from costs less than 500\n";
    cout << "6. Count books with cost more than 500\n";
    cout << "0. Exit\n";
}

int main() {
    int N = 0;
    int* costs = nullptr;

    while (true) {
        displayMenu();
        int choice;
        cin >> choice;

        switch (choice) {
            case 1:
                if (costs != nullptr) {
                    delete[] costs;
                }
                cout << "Enter the number of books: ";
                cin >> N;
                costs = new int[N];
                cout << "Enter the costs of the books:\n";
                for (int i = 0; i < N; i++) {
                    cin >> costs[i];
                }
                break;

            case 2:
                if (costs != nullptr) {
                    sortDescending(costs, N);
                    cout << "Costs of books in descending order:\n";
                    for (int i = 0; i < N; i++) {
                        cout << costs[i] << " ";
                    }
                    cout << endl;
                } else {
                    cout << "Please insert book costs first.\n";
                }
                break;

            case 3:
                if (costs != nullptr) {
                    int* costsLessThan500 = new int[N];
                    int sizeLessThan500 = copyCostsLessThan500(costs, N, costsLessThan500);
                    cout << "Costs of books less than 500:\n";
                    for (int i = 0; i < sizeLessThan500; i++) {
                        cout << costsLessThan500[i] << " ";
                    }
                    cout << endl;
                    delete[] costsLessThan500;
                } else {
                    cout << "Please insert book costs first.\n";
                }
                break;

            case 4:
                if (costs != nullptr) {
                    int* costsLessThan500 = new int[N];
                    int sizeLessThan500 = copyCostsLessThan500(costs, N, costsLessThan500);
                    int* uniqueCostsWithTemp = new int[sizeLessThan500];
                    int sizeUniqueWithTemp = removeDuplicatesUsingTempArray(costsLessThan500, sizeLessThan500, uniqueCostsWithTemp);
                    cout << "Costs of books less than 500 (duplicates removed using temp array):\n";
                    for (int i = 0; i < sizeUniqueWithTemp; i++) {
                        cout << uniqueCostsWithTemp[i] << " ";
                    }
                    cout << endl;
                    delete[] costsLessThan500;
                    delete[] uniqueCostsWithTemp;
                } else {
                    cout << "Please insert book costs first.\n";
                }
                break;

            case 5:
                if (costs != nullptr) {
                    int* costsLessThan500 = new int[N];
                    int sizeLessThan500 = copyCostsLessThan500(costs, N, costsLessThan500);
                    int newSizeLessThan500 = removeDuplicatesWithoutTempArray(costsLessThan500, sizeLessThan500);
                    cout << "Costs of books less than 500 (duplicates removed without temp array):\n";
                    for (int i = 0; i < newSizeLessThan500; i++) {
                        cout << costsLessThan500[i] << " ";
                    }
                    cout << endl;
                    delete[] costsLessThan500;
                } else {
                    cout << "Please insert book costs first.\n";
                }
                break;

            case 6:
                if (costs != nullptr) {
                    int countMoreThan500 = countBooksMoreThan500(costs, N);
                    cout << "Number of books with cost more than 500: " << countMoreThan500 << endl;
                } else {
                    cout << "Please insert book costs first.\n";
                }
                break;

            case 0:
                if (costs != nullptr) {
                    delete[] costs;
                }
                return 0;

            default:
                cout << "Invalid choice. Please try again.\n";
        }
    }
    return 0;
}
