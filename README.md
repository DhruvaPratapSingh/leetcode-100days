## link
[click here](https://leetcode.com/problems/merge-sorted-array/submissions/1341799842/?envType=study-plan-v2&envId=top-interview-150)

# code
```
console.log("hello World !")
```

## day 48 ✅🚀
[problem](https://leetcode.com/problems/uncommon-words-from-two-sentences/description/?envType=daily-question&envId=2024-09-17)

# code 🧑‍💻🧑‍💻
```
vector<string> uncommonFromSentences(string s1, string s2) {
       unordered_map<string,int>m;
      int i=0,j=0,n=s1.size(),mp=s2.size();
    //   string temp="";
      while(j<n){
        if(s1[j]==' '){
            string str=s1.substr(i,j-i);
            m[str]++;
            i=j+1;
        }
        j++;
      }
      string str=s1.substr(i,j-i);
      m[str]++;
      i=0,j=0;
      while(j<mp){
        if(s2[j]==' '){
            string str=s2.substr(i,j-i);
            m[str]++;
            i=j+1;
        }
        j++;
      }
      string str2=s2.substr(i,j-i);
      m[str2]++;
       vector<string>ans;
       for(auto &ele:m){
        cout<<ele.first<<" ";
       if(ele.second==1)ans.push_back(ele.first);
       }
       return ans;
    }
```

## day 49 ⤵️⤵️
[problem link](https://leetcode.com/problems/largest-number/description/?envType=daily-question&envId=2024-09-18)

# code 🚀💯
```
 string largestNumber(vector<int>& nums) {
        vector<string>ans;
        for(int &ele:nums){
            ans.push_back(to_string(ele));
        }
        sort(ans.begin(),ans.end(),[&](string &a,string &b){
            return a+b>b+a;
        });
        string res="";
        for(string &str:ans)res+=str;
        if(res[0]=='0')return "0";
        return res;
    }
```


## day 50 ⤵️⤵️
[problem link](https://leetcode.com/problems/different-ways-to-add-parentheses/description/?envType=daily-question&envId=2024-09-19)

# code 🚀💯

```
vector<int>helper(string str){
    vector<int>ans;
    for(int i=0;i<str.size();i++){
        char ch=str[i];
        if(ch=='+' || ch=='-' || ch=='*'){
            vector<int>v1=helper(str.substr(0,i));
            vector<int>v2=helper(str.substr(i+1));

            for(int &ele:v1){
                for(int &ele2:v2){
                    if(ch=='+')ans.push_back(ele+ele2);
                    else if(ch=='-')ans.push_back(ele-ele2);
                    else if(ch=='*')ans.push_back(ele*ele2);
                }
            }
        }
    }
    if(ans.size()==0){
        ans.push_back(stoi(str));
    }
    return ans;
}
    vector<int> diffWaysToCompute(string expression) {
        vector<int>res=helper(expression);
        return res;
    }
```

## day 51 ![SadCatGIF](https://github.com/user-attachments/assets/644421a7-81dd-4c0a-a410-2c4835d91232)

[problem link](https://leetcode.com/problems/shortest-palindrome/?envType=daily-question&envId=2024-09-20)

# first read kmp algorythm which makes easy to tackle it ⤵️💯
[kmp algorythm](https://www.geeksforgeeks.org/kmp-algorithm-for-pattern-searching/)

# code ![CoolImGIF (2)](https://github.com/user-attachments/assets/d80ac3ee-5b73-4231-983d-4fabace7b71f)
```
 vector<int> LPS(string pat) {
        int n = pat.size();
        vector<int> lps(n, 0);
        int i = 1, j = 0;

        while (i < n) {
            if (pat[i] == pat[j]) {
                lps[i++] = ++j;
            } else {
                if (j == 0) {
                    lps[i++] = 0;
                } else {
                    j = lps[j - 1];
                }
            }
        }
        return lps;
    }
    string shortestPalindrome(string s) {
         int n=s.size();
      
         if (s.empty()) return "";
        string revs = s;
        reverse(revs.begin(), revs.end());
        string combined = s + "#" + revs;
        vector<int> lps = LPS(combined);
        int len = lps.back(); 
        string to_add = s.substr(len); 
        reverse(to_add.begin(), to_add.end());

        return to_add + s;
    }
```

## day 52 💯🎉
[problem link](https://leetcode.com/problems/lexicographical-numbers/description/?envType=daily-question&envId=2024-09-21)

# code ☠️🚀
```
 vector<int> lexicalOrder(int n) {
        vector<int>ans;
        int ele=1;
        while(ans.size()<n){
            ans.push_back(ele);
            if(ele*10<=n){
                ele*=10;
            }
            else if(ele+1<=n and ele%10!=9){
                ele++;
            }
            else{
                while((ele/10)%10==9){
                    ele/=10;
                }
                ele=ele/10+1;
            }
        }
        return ans;
    }
```

## day 53 🤺☠️

[problem link](https://leetcode.com/problems/k-th-smallest-in-lexicographical-order/description/?envType=daily-question&envId=2024-09-22)

# code 👩‍💻➕

```
int f(int prefix, int n) {
        long long current=prefix, next = prefix + 1;
        int count=0;
        while (current<=n) {
            count+=min(n+ 1LL,next)-current;
            current*=10;
            next*=10;
        }
        return count;
    }
    int findKthNumber(int n, int k) {
        int current=1;
        k--;
        while (k>0) {
            int count =f(current, n);
            if (count<=k) {
                current++;
                k-= count;
            }
            else{
                current*= 10;
                k--;
            }
        }
        return current;
    }
```

## day 54 
[problem link](https://leetcode.com/problems/extra-characters-in-a-string/description/?envType=daily-question&envId=2024-09-23)

# code

```
 int minExtraChar(string s, vector<string>& d) {
unordered_set<string>dic(d.begin(),d.end());
int n=s.size();
vector<int>dp(n+1,0);
for(int i=1;i<=n;i++){
    dp[i]=dp[i-1]+1;
    for(int j=0;j<i;j++){
        string str=s.substr(j,i-j);
        if(dic.find(str)!=dic.end()){
            dp[i]=min(dp[i],dp[j]);
        }
    }
}
return dp[n];
    }
```

## day 55

[problem link](https://leetcode.com/problems/find-the-length-of-the-longest-common-prefix/description/?envType=daily-question&envId=2024-09-24)

# code
# using trie ✅💯
```
    class TrieNode {
public:
    TrieNode* children[10];  // Digits 0-9

    TrieNode() {
        for (int i = 0; i < 10; ++i) {
            children[i] = nullptr;
        }
    }
};

class Solution {
private:
    TrieNode* root;

    // Insert a number's string representation into the Trie
    void insert(const string& numStr) {
        TrieNode* node = root;
        for (char c : numStr) {
            int digit = c - '0';
            if (node->children[digit] == nullptr) {
                node->children[digit] = new TrieNode();
            }
            node = node->children[digit];
        }
    }

    // Find the longest common prefix between a number and the Trie
    int getLongestPrefix(const string& numStr) {
        TrieNode* node = root;
        int commonLength = 0;
        for (char c : numStr) {
            int digit = c - '0';
            if (node->children[digit] != nullptr) {
                commonLength++;
                node = node->children[digit];
            } else {
                break;  // Stop as soon as we cannot follow the Trie
            }
        }
        return commonLength;
    }

public:
    Solution() {
        root = new TrieNode();
    }

    // Find the longest common prefix length
    int longestCommonPrefix(vector<int>& arr1, vector<int>& arr2) {
        // Insert all numbers from arr1 into the Trie
        for (int num : arr1) {
            insert(to_string(num));
        }

        // Find the longest common prefix for each number in arr2
        int maxLength = 0;
        for (int num : arr2) {
            maxLength = max(maxLength, getLongestPrefix(to_string(num)));
        }

        return maxLength;
    }
};
```

# using map 🤺🫵
```
int longestCommonPrefix(vector<int>& arr1, vector<int>& arr2) {
        unordered_map<string,int>m;
        int n=arr1.size();
        int p=arr2.size();
        for(int i=0;i<n;i++){
            string a=to_string(arr1[i]);
            for(int j=0;j<a.size();j++){
                m[a.substr(0,j+1)]=1;
            }
        }
        int maxi=0;
        for(int i=0;i<p;i++){
            string a=to_string(arr2[i]);
            for(int j=0;j<a.size();j++){
                if(m[a.substr(0,j+1)]){
                    maxi=max(maxi,j+1);
                }
            }
        }
        return maxi;
    }
```

# bilkul brute force ❌❌
```
class Solution {
public:
    int helper(string &s,string &p){
        int cnt=0;
        for(int i=0;i<min(s.size(),p.size());i++){
            if(s[i]==p[i]){
                cnt++;
            }
            else break;
        }
        return cnt;
    }
    int longestCommonPrefix(vector<int>& arr1, vector<int>& arr2) {
        vector<pair<string,string>>p;
        for(int i=0;i<arr1.size();i++){
            for(int j=0;j<arr2.size();j++){
                p.push_back({to_string(arr1[i]),to_string(arr2[j])});
            }
        }
        int c=0;
      for(int i=0;i<p.size();i++){
       c=max(c,helper(p[i].first,p[i].second));
      }
        return c;
    }
};
```
## day 56
[problem link](https://leetcode.com/problems/my-calendar-i/description/?envType=daily-question&envId=2024-09-26)
# code
```
class MyCalendar {
public:
    // vector<pair<int,int>>p;
    unordered_map<int,int>m;
    MyCalendar() {
        
    }
    
    bool book(int start, int end) {
      for(auto ele:m){
        if(ele.first<end and ele.second>start)return 0;
      }
      m[start]=end;
      return 1;
    }
};
```
## day 57 🚀✅
[problem link](https://leetcode.com/problems/my-calendar-ii/)

# code☠️👩‍💻
```
vector<pair<int,int>> events;
    vector<pair<int,int>> overlaps;
    MyCalendarTwo() {
        
    }
    
    bool book(int start, int end) {
        for(auto& p:overlaps){
            if(start<p.second && p.first<end){return false;}
        }
        for(auto& p:events){
            if (start<p.second && p.first<end){
                //common overlap interval inserted
                overlaps.push_back({max(start, p.first),min(end, p.second)});
            }
        }
        events.push_back({start,end});
        return true;
    }
};

```
## day 58
[problem link](https://leetcode.com/problems/my-calendar-ii/?envType=daily-question&envId=2024-09-28)

# code
```
class MyCalendarTwo {
public:
 vector<pair<int,int>> events;
    vector<pair<int,int>> overlaps;
    MyCalendarTwo() {
        
    }
    
    bool book(int start, int end) {
        for(auto& p:overlaps){
            if(start<p.second && p.first<end){return false;}
        }
        for(auto& p:events){
            if (start<p.second && p.first<end){
                //common overlap interval inserted
                overlaps.push_back({max(start, p.first),min(end, p.second)});
            }
        }
        events.push_back({start,end});
        return true;
    }
};
```

## day 59

[problem link](https://leetcode.com/problems/design-circular-deque/?envType=daily-question&envId=2024-09-28)

# code
```
class MyCircularDeque {
public:
  deque<int>dq;
  int size;
    MyCircularDeque(int k) {
        size=k;
    }
    
    bool insertFront(int value) {
        if(dq.size()<size){
            dq.push_front(value);
            return 1;
        }
        return 0;
    }
    
    bool insertLast(int value) {
        if(dq.size()<size){
            dq.push_back(value);
            return 1;
        }
        return 0;
    }
    
    bool deleteFront() {
        if(dq.size()>0){
            dq.pop_front();
            return 1;
        }
        return 0;
    }
    
    bool deleteLast() {
        if(dq.size()>0){
            dq.pop_back();
            return 1;
        }
        return 0;
    }
    
    int getFront() {
        if(dq.size()>0){
            return dq.front();
        }
        return -1;
    }
    
    int getRear() {
        if(dq.size()>0){
            return dq.back();
        }
        return -1;
    }
    
    bool isEmpty() {
        return dq.size()==0;
    }
    
    bool isFull() {
        return dq.size()==size;
    }
};
```
## day 60
[problem link](https://leetcode.com/problems/all-oone-data-structure/description/?envType=daily-question&envId=2024-09-29)

# code
```
class AllOne {
    unordered_map<string,int>m;
    map<int,unordered_set<string>>s;
public:

    AllOne() {
        
    }
    
    void inc(string key) {
        int cnt=m[key]++;
        if(cnt>0)s[cnt].erase(key);
        s[cnt+1].insert(key);
        if(s[cnt].empty())s.erase(cnt);
    }
    
    void dec(string key) {
        int cnt=m[key]--;
        if(cnt>0)s[cnt].erase(key);
        if(cnt==1)m.erase(key);
        else s[cnt-1].insert(key);
        if(s[cnt].empty())s.erase(cnt);
    }
    
    string getMaxKey() {
        return s.empty() ? "":*(s.rbegin()->second.begin());
    }
    
    string getMinKey() {
        return s.empty() ? "":*(s.begin()->second.begin());
    }
};
```
## day 61
[problem link](https://leetcode.com/problems/design-a-stack-with-increment-operation/description/?envType=daily-question&envId=2024-09-30)

# code
```
class CustomStack {
    vector<int>ans;
    int size;
public:
    CustomStack(int maxsize) {
        size=maxsize;
    }
    
    void push(int x) {
        if(ans.size()<size){
            ans.push_back(x);
        }
    }
    
    int pop() {
        int n=ans.size();
        if(n){
            int val=ans[n-1];
            ans.pop_back();
            return val;
        }
        return -1;
    }
    
    void increment(int k, int val) {
        int i=0;
        int n=ans.size();
       while(i<n and k--){
        ans[i]+=val;
        i++;
       }
    }
};
```
## day 62

## day 63

[problem link](https://leetcode.com/problems/rank-transform-of-an-array/description/?envType=daily-question&envId=2024-10-02)

# code
```
vector<int> arrayRankTransform(vector<int>& arr) {
      unordered_map<int, int> numToRank;
        // Deduplicate and sort arr
        set<int> nums(arr.begin(), arr.end());
        int rank = 1;
        for (auto num : nums) {
            numToRank[num] = rank;
            rank++;
        }
        for (int i = 0; i < arr.size(); i++) {
            arr[i] = numToRank[arr[i]];
        }
        return arr;
    }
```
## day 64

[problem link](https://leetcode.com/problems/make-sum-divisible-by-p/description/)


