# Print all subsequences with given sum

```c++
#include<iostream>
#include<vector>
using namespace std;

void printS(int ind,vector<int>&ds,int s,int sum,int arr[],int n){
    //base case 
    if(ind == n){
        if(s == sum){
            for(auto it:ds)cout<<it<<" ";
            cout<<endl;
        }
         return;
    }
    //pick 
   ds.push_back(arr[ind]);
   s += arr[ind];
   printS(ind+1,ds,s,sum,arr,n);
   ds.pop_back();
   s-=arr[ind];
   //not pick
   printS(ind+1,ds,s,sum,arr,n);
}
int main(){
    int arr[] = {1,2,1,1,1,1,3,2};
    int n = 8;
    int sum = 5;
    vector<int>ds;
    printS(0,ds,0,sum,arr,n);
    return 0;
}

```

# print any one sequence with given sum
```c++
#include<iostream>
#include<vector>
using namespace std;

bool printS(int ind,vector<int>&ds,int s,int sum,int arr[],int n){
    //base case  - codition satisfied
    if(ind == n){
           if(s == sum){
            for(auto it:ds)cout<<it<<" ";
            cout<<endl;
            return true;
        }
        //condition not satisfied
        else return false;
    }
    //pick 
   ds.push_back(arr[ind]);
   s += arr[ind];
   if(printS(ind+1,ds,s,sum,arr,n) == true){
    return true;
   }
   ds.pop_back();
   s-=arr[ind];
   //not pick
   if(printS(ind+1,ds,s,sum,arr,n) == true){
    return true;
   }
   return false;
}
int main(){
    int arr[] = {1,2,1,1,1,1,3,2};
    int n = 8;
    int sum = 5;
    vector<int>ds;
    printS(0,ds,0,sum,arr,n);
    return 0;
}

```