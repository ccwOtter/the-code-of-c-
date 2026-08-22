# set常用操作代码举例：
```cpp
#include <bits/stdc++.h> 
using namespace std;

int main(){
    set<int> st = {5, 2, 8, 1, 9, 2};
    set<int,greater<int>> stg = {5, 2, 8, 1, 9, 2};
    set<int>::iterator it;
    set<int>::reverse_iterator rit;//反向迭代器
    
    //set不支持下标索引
    for (it = st.begin(); it != st.end(); it++) {//也可以不定义it，直接用auto it=st.begin();
        cout << *it << " "; 
    }
    cout<<endl;
    for (rit = st.rbegin(); rit != st.rend(); rit++) {//也可以不定义rit，直接用auto rit=st.rbegin();
        cout << *rit << " "; 
    }
    cout<<endl;
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    for (int x : stg) {
        cout << x << " ";
    }
    cout<<endl;
    
    cout<<st.empty()<<endl;
    
    cout<<st.size()<<endl;
    
    cout<<st.count(4)<<endl;
    
    st.insert(3);
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    
    st.erase(8);
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    if (!st.empty()) {
        st.erase(st.begin());
    }
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    
    set<int>::iterator it1,it2;
    it1=st.find(3);//也可以不定义迭代器，直接使用 auto it1=st.find(3);
    if (it1 != st.end()) cout << *it1 << endl;
    else cout << "not found" << endl;
    it2=st.find(8);
    if (it2 != st.end()) cout << *it2 << endl;
    else cout << "not found" << endl;

    set<int> st1 = {105, 102, 108, 101, 109, 102};
    st.swap(st1);
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    
    st.erase(st.begin(),st.end());//相当于st.clear()
    for (int x : st) {
        cout << x << " ";
    }
    cout<<endl;
    
    return 0;    
}
```
# map常用操作代码举例：
```cpp
#include <bits/stdc++.h> 
using namespace std;

int main(){
    
    map<string,int> mp = {{"apple", 1}, {"banana", 2}, {"cherry", 3}};
    map<string,int,greater<string>> mpg = {{"apple", 1}, {"banana", 2}, {"cherry", 3}};
    
    for (auto it = mp.begin(); it != mp.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    for (auto rit = mp.rbegin(); rit != mp.rend(); rit++) {
        cout << rit->first << " -> " << rit->second << endl;
    }
    for (auto it = mpg.begin(); it != mpg.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    
    cout << mp["apple"] << endl;//用键作为下标索引
    cout << mp["banana"] << endl;
    cout << mp["pear"] << endl;//输出0
    cout << mp.at("apple") << endl;
    //cout << mp.at("pear") << endl;会抛异常
    
    cout<<mp.empty()<<endl;
    
    cout<<mp.size()<<endl;
    
    cout<<mp.count("cherry")<<endl;
    
    mp.insert({"orange",4});
    mp["pear"]=5;
    for (auto it = mp.begin(); it != mp.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    
    mp.erase("cherry");
    for (auto it = mp.begin(); it != mp.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    
    auto it1=mp.find("orange");
    auto it2=mp.find("watermelon");
    if(it1!=mp.end()) mp.erase(it1);
    else cout << "not found" << endl;
    if(it2!=mp.end()) mp.erase(it2);
    else cout << "not found" << endl;
    for (auto it = mp.begin(); it != mp.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    
    mp.erase(mp.begin(),mp.end());//相当于mp.clear()
    for (auto it = mp.begin(); it != mp.end(); it++) {
        cout << it->first << " -> " << it->second << endl;
    }
    
    return 0;    
}
```
