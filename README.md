
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
