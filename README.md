
![image](https://github.com/user-attachments/assets/b6bbf174-b538-4089-85f8-90fad18269b2)

## link
[click here](https://leetcode.com/problems/merge-sorted-array/submissions/1341799842/?envType=study-plan-v2&envId=top-interview-150)

# code
```
console.log("hello World !")
```

## day 48
[problem](https://leetcode.com/problems/uncommon-words-from-two-sentences/description/?envType=daily-question&envId=2024-09-17)

# code
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
