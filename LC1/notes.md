# Key: Hash table  

## 1. What is Hash Table  
https://www.youtube.com/watch?v=MfhjkfocRR0  
https://zh.wikipedia.org/wiki/%E5%93%88%E5%B8%8C%E8%A1%A8

## 2.Top-k and Hash Table
http://blog.csdn.net/v_JULY_v/article/details/6256463  
Merge Sort O(NlogN), Traversal O(N), Binary Search O(logN)  
>数组的特点是：寻址容易，插入和删除困难；而链表的特点是：寻址困难，插入和删除容易。  

### 除法散列法
index = value % 16  
### 平方散列法
index = (value * value) >> 28  
### 斐波那契（Fibonacci）散列法  
理想的乘数  
1，对于16位整数而言，这个乘数是40503  
2，对于32位整数而言，这个乘数是2654435769   
3，对于64位整数而言，这个乘数是11400714819323198485  

## 3.Problems on Different OJ
HDU 1280 前m大的数  
Time 0ms Memory 1460K

    #include <stdio.h>
    #include <map>
    #include <string.h>
    using namespace std;
    int N,M;
    int nums[3000];
    int hash_table[10010];
    int main()
    {
        while(~scanf("%d %d",&N,&M))
        {
            memset(hash_table,0,sizeof(hash_table));
            //input
            for(int i=0;i<N;i++)
                scanf("%d",&nums[i]);
            //solution O(N^2)
            for(int i=0;i<N-1;i++)
                for(int j=i+1;j<N;j++)
                {
                    hash_table[nums[i]+nums[j]]++;
                }
            //output
            for(int i=10010;i>=0&&M!=0;i--)
                while(hash_table[i]>0&&M)
                {
                    hash_table[i]--;
                    M--;
                    if(M==0)
                        printf("%d\n",i);
                    else
                        printf("%d ",i);
                }

        }
        return 0;
    }  

hash+最大堆，STL堆  
http://www.acmsearch.com/article/show/10246  
http://blog.csdn.net/whyorwhnt/article/details/8741352

HDU 1425 sort  
HDU 3785 寻找大富翁  
