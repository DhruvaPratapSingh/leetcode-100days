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
