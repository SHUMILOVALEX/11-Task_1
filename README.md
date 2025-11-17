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
Task 11.3
#include <list>
#include <iostream>
#include <string>
#include <algorithm>

using namespace std;

int main() {
    list<string> listok = {"Ivanov", "Petrov", "Sidorov", "Alekseev", "Borisov"};
    listok.sort();
    for (string i : listok) {
        cout << i << " ";
    }
    cout <<endl<< "New list: ";
    listok.remove_if([](const string& name){return name[0] == 'A';});
    for (string i : listok) {
        cout << i << " ";
    }
}
Task 11.4
#include <forward_list>
#include <iostream>
using namespace std;
int main() {
    forward_list<int> mylist = {};
    mylist.push_front(5);
    for ( int i = 4; i != 0;--i) {
        mylist.insert_after(mylist.before_begin(), i);
    }
    for (int i : mylist) {
        cout << i;
    }
}
Task 11.5
#include <list>
#include <iostream>
#include <algorithm>
using namespace std;
int main() {
    list<int> a = {1, 3, 5, 7};
    list<int> b = {2, 3, 6, 7, 8};
    a.merge(b);
    a.sort();
    a.unique();
    a.remove_if([](int x){return x > 6;});
    for (int i : a) {
        cout<< i;
    }
return 0;}
Task 12.1

#include <iostream>
#include <fstream>
#include <string>
#include <algorithm>
#include <cctype>
using namespace std;

int main() {
    ifstream file("C:/Users/1/Desktop/input.txt");
    if (!file.is_open()) {
        cerr << "Unable to open input file!" << endl;
        return 1;
    }

ofstream file1("C:/Users/1/Desktop/output.txt");
    if (!file1.is_open()) {
        cerr << "Unable to open output file!" << endl;
        file.close();
        return 1;
    }
    string line;
    string line_find = "useragreement";
    while (file >> line) {
        cout << "Reading: " << line << endl;
        string lower_line = line;
        transform(lower_line.begin(), lower_line.end(), lower_line.begin(),
                  [](unsigned char c) { return tolower(c); });
        size_t pos = lower_line.find(line_find);
        if (pos != string::npos) {
            line.replace(pos, line_find.size(), "");
            cout << "Modified: " << line << endl;
        }
        if (!(file1 << line << " ")) {
            cerr << "Failed to write to output file!" << endl;
            file.close();
            file1.close();
            return 1;
        }
    }
    file.close();
    file1.close();
    if (file1.fail()) {
        cerr << "Error closing output file!" << endl;
        return 1;
    }
    cout << "Success! Output written to output.txt" << endl;
    return 0;
}
Task 12.2
#include <iostream>
#include <string>
#include <fstream>
#include <vector>
using namespace std;
int main() {
    ifstream file("input1.txt");
    if (!file.is_open()) {
        cout << "File could not be opened" << endl;
        return 1;
    }
    ifstream file1("input2.txt");
    if (!file1.is_open()) {
        cout << "File could not be opened" << endl;
        return 1;
    }
    string line1;
    string line2;
    file1 >> line1;
    file1 >> line2;
    if (line1.find(line2) != string::npos){
        cout << "yes" << endl;
}
    else
        cout << "no" << endl;
file.close();
}
Task 12.3
#include <iostream>
#include <string>
#include <fstream>
using namespace std;

string toBinary(int n) {
    if (n == 0) return "0";
    string binary;
    while (n > 0) {
        binary = (n % 2 == 0 ? "0" : "1") + binary;
        n /= 2;
    }
    return binary;
}

int main() {
    ofstream file("C:/Users/1/Desktop/input2.txt");
    if (!file.is_open()) {
        cout << "Error opening file" << endl;
        return 1;
    }

ifstream file1("C:/Users/1/Desktop/input1.txt");
    if (!file1.is_open()) {
        cout << "Error opening file" << endl;
        file.close();
        return 1;
    }
    string line1;
    getline(file1, line1);
    for (char ch : line1) {
        if (isdigit(ch)) {
            int digit = ch - '0';
            string binary = toBinary(digit);
            file << binary;
        } else {
            file << ch;
        }
    }
    file.close();
    file1.close();
    return 0;
}
