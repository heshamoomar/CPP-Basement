#include <iostream>
#include <cstdlib>
#include <ctime>

using namespace std;
int RandomNumber(int From, int To) {
    int randNum = rand() % (To - From + 1) + From;
    return randNum;
}

void FillArrayWithRandomNumbers(int arr[100], int& arrLength) {
    cout << "\nEnter number of elements:\n";
    cin >> arrLength;
    for (int i = 0; i < arrLength; i++)
        arr[i] = RandomNumber(1, 100);
}

void PrintArray(int arr[100], int arrLength) {
    for (int i = 0; i < arrLength; i++)
        cout << arr[i] << " ";
    cout << "\n";
}

bool isPrime(int n) {
    for (int i = 2; i <= sqrt(n); i++)
    {
        if (n % i == 0)
            return false;
    }
    return true;
}

void AddArrayElement(int Number, int arr[100], int& arrLength) {
    arr[arrLength] = Number;
    arrLength++;
}
void CopyPrimesInArrayUsingAddArrayElement(int arr1[100], int arr2[100], int arr1Length, int& arr2Length) {
    for (int i = 0; i < arr1Length; i++)
        if (isPrime(arr1[i]))
            AddArrayElement(arr1[i], arr2, arr2Length);
}
int main() {
    srand((unsigned)time(NULL));

    int arr[100];
    int arr2[100];

    int arr1Length = 0;
    int arr2Length = 0;
    FillArrayWithRandomNumbers(arr, arr1Length);
    CopyPrimesInArrayUsingAddArrayElement(arr, arr2, arr1Length, arr2Length);

    cout << "\nArray 1 elements:\n";
    PrintArray(arr, arr1Length);
    cout << "\nArray 2 elements after copy:\n";
    PrintArray(arr2, arr2Length);
}
