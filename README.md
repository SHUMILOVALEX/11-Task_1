#Task 11. 1
#include<iostream>
#include<array>
#include<random>
#include <numeric>
using namespace std;
int main() {
    srand(time(NULL));
    array<double,10> a;
    for(int i=0;i<10;i++){
    a[i]=0.1 * (rand() % 101);
}
    for(auto i : a) {
        cout<<i<<" ";
    }
    double num = accumulate(a.begin(),a.end(),0.00)/10 ;
    cout<<endl;
    cout<< num;
}
Task 11.2
#include <iostream>
#include <deque>
#include <string>
#include <limits>   
using namespace std;

int main() {
    srand(time(NULL));
    deque<string> arr = {"10 banana", "3 orange"};
    bool O = true;

   while (O) {
        string mainChoice;
        string urgent;
        string order;
       cout << "Would you like to place an order? Answer 'Yes' or 'No': ";
        cin >> mainChoice;
        cin.ignore(numeric_limits<streamsize>::max(), '\n'); // очищаем буфер
        if (mainChoice == "Yes") {
            cout << "Urgent order? Answer 'Yes' or 'No': ";
            getline(cin, urgent);
            cout << "Your order: ";
            getline(cin, order);
            if (urgent == "Yes") {
                arr.push_front(order);
            } else {
                arr.push_back(order);
            }
        } else {
            O = false;
        }
        cout << "\nCurrent orders:\n";
        for (const auto& x : arr) {
            cout << " - " << x << endl;
        }
        cout << endl;
    }

    return 0;
}
