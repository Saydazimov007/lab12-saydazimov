# lab12-saydazimov
#include <iostream>
#include <vector>
#include <string>
#include <unordered_map>
#include <cctype>
#include <cmath>
using namespace std;

     //problem2
int evenCount(const int* a, int size) {
    int count = 0;
    const int* ptr = a;


    for (int i = 0; i < size; ++i) {
        if (*ptr % 2 == 0) {
            count++;
        }
        ptr++;
    }
    return count;
     }

    //problem3

         bool isMirrored(const int* a, const int* b, int size) {
             const int* ptr1 = a;
             const int* ptr2 = b + size - 1;

             for (int i = 0; i < size; ++i) {

                 if (*ptr1 != *ptr2) {
                     return false;
                 }

                 ptr1++;
                 ptr2--;
             }


             return true;
         }

         //problem4

void sumArrays(const double* arr1, const double* arr2, double* sum, int size) {
    for (int i = 0; i < size; ++i) {
        sum[i] = arr1[i] + arr2[i];
    }

    //problem5
    //
void swap(int *arr1, int *arr2, int size){
        for (int i = 0; i < size; ++i) {
            int temp = *(arr1 + i);
            *(arr1 + i) = *(arr2 + i);
            *(arr2 + i) = temp;
        }
    }


    //problem6

    bool is_in(const int *arr1, const int *arr2, int size1, int size2) {
        const int *p1 = arr1;
        const int *p2 = arr2;


        while (p1 - arr1 < size1) {
            bool found = false;

            while (p2 - arr2 < size2) {
                if (*p1 == *p2) {
                    found = true;
                    break;
                }
                p2++;
            }

            if (!found) {
                return false;
            }

            p1++;
        }


        return true;
    }

    //problem7

    void power(double *n, const int *p) {
        double result = 1.0;
        int power = *p;


        while (power > 0) {
            result *= *n;
            power--;
        }


        *n = result;
    }
    //problem8

    vector<int> addOne(vector<int> &v){
        int carry = 1;
        int n = v.size();


        for (int i = n - 1; i >= 0; --i) {
            int sum = v[i] + carry;
            v[i] = sum % 10;
            carry = sum / 10;


            if (carry == 0)
                break;
        }


        if (carry > 0)
            v.insert(v.begin(), carry);

        return v;
    }

    //problem9

    string normalize(const string &word) {
        string normalizedWord = word;


        normalizedWord[0] = toupper(normalizedWord[0]);


        for (size_t i = 1; i < normalizedWord.size(); ++i) {
            normalizedWord[i] = tolower(normalizedWord[i]);
        }

        return normalizedWord;
    }



    //problem10

    int singleNum(vector<int> &vec) {
        unordered_map<int, int> countMap;


        for (int num: vec) {
            countMap[num]++;
        }


        for (const auto &pair: countMap) {
            if (pair.second == 1) {
                return pair.first;
            }
        }


        return -1;
    }





//problem1

    int main() {
        const int SIZE = 10;
        float *ptr, arr[SIZE];

        ptr = arr;


        cout << "Enter the grades of 10 students for the Midterm exam:\n";
        for (int i = 0; i < SIZE; ++i) {
            cout << "Enter grade for student " << i + 1 << ": ";
            cin >> *(ptr + i);
        }



        for (int i = 0; i < SIZE; ++i) {
            *(ptr + i) = *(ptr + i) * 0.3;
        }


        cout << "\nOverall grades considering Midterm weight (30%):\n";
        for (int i = SIZE - 1; i >= 0; --i) {
            cout << "Student " << SIZE - i << ": " << *(ptr + i) << endl;
        }

        //problem2
        cout << "Enter the size of the array: ";
        cin >> size;

        cout << "Enter the elements of the array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr[i];
        }


        cout << "Number of even numbers: " << evenCount(reinterpret_cast<const int *>(arr), size) << endl;

        //problem3

        int size;
        cout << "Enter the size of the arrays: ";
        cin >> size;

        int arr1[size];

        cout << "Enter the elements of the first array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr1[i];
        }

        cout << "Enter the elements of the second array (in reverse order):\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr2[i];
        }


        cout << "Arrays are mirrored: " << (isMirrored(arr1, arr2, size) ? "Yes" : "No") << endl;


        //problem4

        int size;
        cout << "Enter the size of the arrays: ";
        cin >> size;

        double arr2[size], sum[size];

        cout << "Enter the elements of the first array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr1[i];
        }

        cout << "Enter the elements of the second array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr2[i];
        }


        sumArrays(reinterpret_cast<const double *>(arr1), reinterpret_cast<const double *>(arr2), sum, size);


        cout << "Element-wise sum of the arrays:\n";
        for (int i = 0; i < size; ++i) {
            cout << sum[i];
        }
        cout << endl;

        //problem5

        int size;
        cout << "Enter the size of the arrays: ";
        cin >> size;

        int arr1[size], arr2[size];

        cout << "Enter the elements of the first array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr1[i];
        }

        cout << "Enter the elements of the second array:\n";
        for (int i = 0; i < size; ++i) {
            cin >> arr2[i];
        }


        swap(arr1, arr2, size);


        cout << "Swapped arrays:\n";
        cout << "Array 1: ";
        for (int i = 0; i < size; ++i) {
            cout << arr1[i] << " ";
        }
        cout << endl;
        cout << "Array 2: ";
        for (int i = 0; i < size; ++i) {
            cout << arr2[i] << " ";
        }
        cout << endl;

        //problem6

        int size1, size2;
        cout << "Enter the size of the first array: ";
        cin >> size1;
        cout << "Enter the size of the second array: ";
        cin >> size2;

        int arr1[size1], arr2[size2];

        cout << "Enter the elements of the first array:\n";
        for (int i = 0; i < size1; ++i) {
            cin >> arr1[i];
        }

        cout << "Enter the elements of the second array:\n";
        for (int i = 0; i < size2; ++i) {
            cin >> arr2[i];
        }


        cout << "All elements of arr1 are present in arr2: " << (is_in(arr1, arr2, size1, size2) ? "Yes" : "No")
             << endl;


        //problem7

        double base;
        int exponent;

        cout << "Enter the base: ";
        cin >> base;

        cout << "Enter the exponent: ";
        cin >> exponent;


        power(&base, &exponent);

        cout << "Result: " << base << endl;


        //problem8

        vector<int> v;

        cout << "Enter the digits of the number separated by spaces (from right to left): ";
        int digit;

        while (cin >> digit) {
            v.push_back(digit);
        }


        vector<int> result = addOne(v);


        cout << "Result: ";
        for (int digit: result) {
            cout << digit;
        }
        cout << endl;


// problem9

        string input;
        cout << "Enter a word to normalize: ";
        cin >> input;

        string normalized = normalize(input);
        cout << "Normalized word: " << normalized << endl;



//problem10

        vector<int> v;
        int t;
        cout << "Enter the elements of the vector (separated by spaces, press any non-integer key to end): ";
        while (cin >> t) {
            v.push_back(t);
        }
        cout << "The single number is: " << singleNum(v) << endl;


        return 0;
    }

}
