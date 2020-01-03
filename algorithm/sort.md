[toc]

# 排序算法

## 1. 十大排序算法概述

排序算法是最基本的算法之一。

排序算法可分为内部排序和外部排序，内部排序是数据记录在内存中进行排序，而外部排序是因排序的数据很大，一次不能容纳全部的排序记录，在排序的过程中需要访问外存。

| 名称     | 数据对象  | 稳定性      | 平均时间复杂度                | 最坏时间复杂度                | 额外空间复杂度 |
| -------- | --------- | ----------- | ----------------------------- | ----------------------------- | -------------- |
| 冒泡排序 | 数组      | 稳定        | O(n<sup>2</sup>)              | O(n<sup>2</sup>)              | O(1)           |
| 选择排序 | 数组/链表 | 不稳定/稳定 | O(n<sup>2</sup>)              | O(n<sup>2</sup>)              | O(1)           |
| 插入排序 | 数组/链表 | 稳定        | O(n<sup>2</sup>)              | O(n<sup>2</sup>)              | O(1)           |
| 堆排序   | 数组      | 不稳定      | O(nlogn)                      | O(nlogn)                      | O(1)           |
| 归并排序 | 数组/链表 | 稳定        | O(nlog<sup>2</sup>n)/O(nlogn) | O(nlog<sup>2</sup>n)/O(nlogn) | O(1)           |
| 快速排序 | 数组      | 不稳定      | O(nlogn)                      | O(n<sup>2</sup>)              | O(logn)        |
| 希尔排序 | 数组      | 不稳定      | O(nlog<sup>2</sup>n)          | O(n<sup>2</sup>)              | O(1)           |
| 计数排序 | 数组/链表 | 稳定        | O(n+m)                        | O(n+m)                        | O(n+m)         |
| 桶排序   | 数组/链表 | 稳定        | O(n)                          | O(n)                          | O(m)           |
| 基数排序 | 数组/链表 | 稳定        | O(k*n)                        | O(n<sup>2</sup>)              |                |

## 2. 冒泡排序

### 2.1 算法流程

* 比较相邻的元素。如果第一个比第二个大，就交换他们两个。

* 对每一对相邻元素作同样的工作，从开始第一对到结尾的最后一对。这步做完后，最后的元素会是最大的数。
* 针对所有的元素重复以上的步骤，除了最后一个。
* 持续每次对越来越少的元素重复上面的步骤，直到没有任何一对数字需要比较。

### 2.2 C++代码

```c++
void bubble_sort(int arr[], int n){

    for(int i= 0; i< n-1; i++){
        for(int j= 0; j< n-i-1; j++){
            if( arr[j] > arr[j+1]){
                int tmp= arr[j];
                arr[j]= arr[j+1];
                arr[j+1]= tmp;
            }
        }
    }

    return;
}
```



## 3. 选择排序

### 3.1 算法流程

* 首先在未排序序列中找到最小（大）元素，存放到排序序列的起始位置。

* 再从剩余未排序元素中继续寻找最小（大）元素，然后放到已排序序列的末尾。

* 重复第二步，直到所有元素均排序完毕

### 3.2 C++代码

```c++
void select_sort(int arr[], int n){

    for(int i=0;i<n-1;i++){
        int min_=i;
        for(int j=i+1;j<n;j++){
            if(arr[j]<arr[min_]){
                min_=j;
            }
        }
        int tmp=arr[i];
        arr[i]=arr[min_];
        arr[min_]=tmp;
    }

    return;
}
```

## 4. 插入排序

### 4.1 算法流程

* 将第一待排序序列第一个元素看做一个有序序列，把第二个元素到最后一个元素当成是未排序序列。

* 从头到尾依次扫描未排序序列，将扫描到的每个元素插入有序序列的适当位置。（如果待插入的元素与有序序列中的某个元素相等，则将待插入元素插入到相等元素的后面。）

### 4.2 C++代码

```C++
void insert_sort(int arr[], int n){

    for(int i=1;i<n;i++){
        int key = arr[i];
        int j=i-1;
        while((j>=0)&&(key<arr[j])){
            arr[j+1]=arr[j];
            j--;
        }
        arr[j+1]=key;

    }

    return ;
}
```

## 5. 希尔排序

### 5.1 算法流程

* 选择一个增量序列 t1，t2，……，tk，其中 ti > tj, tk = 1；

* 按增量序列个数 k，对序列进行 k 趟排序；

* 每趟排序，根据对应的增量 ti，将待排序列分割成若干长度为 m 的子序列，分别对各子表进行直接插入排序。仅增量因子为 1 时，整个序列作为一个表来处理，表长度即为整个序列的长度。

### 5.2 C++代码

```C++
void shell_sort(int arr[], int n){

    for(int det=n>>1;det>0;det>>=1){
        for(int i=det;i<n;i++){
            int tmp=arr[i];
            int j=i-det;
            while((j>=0)&&(arr[j]>tmp)){
                arr[j+det]=arr[j];
                j-=det;
            }
            arr[j+det]=tmp;
        }
    }

    return;
}
```

## 6. 归并排序

### 6.1 算法流程

* 申请空间，使其大小为两个已经排序序列之和，该空间用来存放合并后的序列；

* 设定两个指针，最初位置分别为两个已经排序序列的起始位置；

* 比较两个指针所指向的元素，选择相对小的元素放入到合并空间，并移动指针到下一位置；

* 重复步骤 3 直到某一指针达到序列尾；

* 将另一序列剩下的所有元素直接复制到合并序列尾。

### 6.2 C++代码

```c++
void merge_(int arr[], int l, int mid ,int r){

    int i=l,j=mid+1,k=0;
    int *p = (int*)malloc((r-l+5)*sizeof(int));
    while(i<=mid&&j<=r){
        if(arr[i]<arr[j]){
            *(p+k)=arr[i];
            k++;
            i++;
        }else if(arr[i]>arr[j]){
            *(p+k)=arr[j];
            k++;
            j++;
        }else{
            *(p+k)=arr[i];
            k++;
            i++;
            *(p+k)=arr[j];
            k++;
            j++;
        }
    }
    while(i<=mid){
        *(p+k)=arr[i];
        k++;
        i++;
    }
    while(j<=r){
        *(p+k)=arr[j];
        k++;
        j++;
    }
    for(int c=0;c<k;c++){
        arr[l+c]=p[c];
    }

    free(p);
    return;

}

void merge_sort(int arr[], int l, int r){

    if(l>=r) return;
    else{
        int mid = (l+r)>>1;
        merge_sort(arr, l, mid);
        merge_sort(arr, mid+1, r);
        merge_(arr, l, mid, r);
    }
}
```

## 7. 快速排序

### 7.1 算法流程

* i =L; j = R; 将基准数挖出形成第一个坑a[i]。

* j--由后向前找比它小的数，找到后挖出此数填前一个坑a[i]中。

* i++由前向后找比它大的数，找到后也挖出此数填到前一个坑a[j]中。

* 再重复执行2，3二步，直到i==j，将基准数填入a[i]中。

### 7.2 C++代码

```c++
void quick_sort(int arr[], int l, int r){

    if(l<r){
        int i=l,j=r;
        int x=arr[i];
        while(i<j){
            while(i<j&&arr[j]>=x) j--;
            if(i<j){
                arr[i]=arr[j];
                i++;
            }
            while(i<j&&arr[i]<x) i++;
            if(i<j){
                arr[j]=arr[i];
                j--;
            }
        }
        arr[i]=x;
        quick_sort(arr, l, i-1);
        quick_sort(arr, i+1, r);
    }

}
```

## 8.堆排序

### 8.1 堆

堆排序（Heapsort）是指利用堆这种数据结构所设计的一种排序算法。堆积是一个近似完全二叉树的结构，并同时满足堆积的性质：即子结点的键值或索引总是小于（或者大于）它的父节点。堆排序可以说是一种利用堆的概念来排序的选择排序。分为两种方法：

* 大顶堆：每个节点的值都大于或等于其子节点的值，在堆排序算法中用于升序排列；

* 小顶堆：每个节点的值都小于或等于其子节点的值，在堆排序算法中用于降序排列；

堆排序的平均时间复杂度为 Ο(nlogn)。

### 8.2 算法流程

* 将待排序序列构建成一个堆 H[0……n-1]，根据（升序降序需求）选择大顶堆或小顶堆；

* 把堆首（最大值）和堆尾互换；

* 把堆的尺寸缩小 1，并调用 shift_down(0)，目的是把新的数组顶端数据调整到相应位置；

* 重复步骤 2，直到堆的尺寸为 1。

### C++代码

```c++
void max_heapify(int arr[], int p, int r){

    int f=p,s=(f<<1)+1;
    while(s<=r){
        if(s+1<=r&&arr[s]<arr[s+1]) s++;
        if(arr[f]>arr[s]) return;
        else{
            int tmp=arr[f];arr[f]=arr[s];arr[s]=tmp;
            f=s;
            s=(f<<1)+1;
        }
    }

}

void heap_sort(int arr[], int n){
    for(int i=(n>>1)-1;i>=0;i--){
        max_heapify(arr, i, n-1);
    }
    for(int i=n-1;i>=1;i--){
        int tmp=arr[0];arr[0]=arr[i];arr[i]=tmp;
        max_heapify(arr, 0, i-1);
    }

}
```

## 9. 计数排序

### 9.1 算法流程

* 找出待排序的数组中最大和最小的元素

* 统计数组中每个值为i的元素出现的次数，存入数组C的第i项

* 对所有的计数累加（从C中的第一个元素开始，每一项和前一项相加）

* 反向填充目标数组：将每个元素i放在新数组的第C(i)项，每放一个元素就将C(i)减1

### 9.2 C++代码

**仅支持整数（包括负整数）**

```c++
void count_sort(int arr[], int n){


    int min_=arr[0],max_=arr[0];
    for(int i=1;i<n;i++){
        if(arr[i]>max_) max_=arr[i];
        if(arr[i]<min_) min_=arr[i];
    }

    for(int i=0;i<n;i++){
        arr[i]-=min_;
    }

    int *p = (int*) malloc((max_-min_+5)*sizeof(int));

    for(int i=0;i<=max_-min_;i++) p[i]=0;
    for(int i=0;i<n;i++) p[arr[i]]++;
    for(int i=1;i<=max_-min_;i++) p[i]+=p[i-1];

    int *sarr =(int*) malloc((n+1)*sizeof(int));

    for(int i=n;i>0;i--){	//反向填充的目的是要保证算法的稳定性
        sarr[--p[arr[i-1]]]=arr[i-1];
    }
    for(int i=0;i<n;i++) arr[i]=sarr[i]+min_;

    free(p);
    free(sarr);
}
```

## 10. 桶排序

**ps ：以将0~99这100个数分配到10个桶里为例**

### 10.1 算法流程

* 开辟10个桶的链表空间
* 将每个数除以10的值作为键选定桶并根据个位数的大小插入链表
* 从上到下从左到右将值拷贝至数组

### 10.2 C++代码

```c++
struct Node{
    int value;
    Node* nxt;
};

void bucket_sort(int arr[], int n){

    int bkn = 10;

    Node *lst = (Node*) malloc((bkn+1)*sizeof(Node));
    for(int i=0;i<=bkn;i++) lst[i].nxt = NULL;
    Node *cur = NULL;
    Node *p = NULL;
    for(int i=0;i<n;i++){
        int tmp = arr[i];
        p = lst + tmp/10;
        cur = p->nxt;
        while(p){
            if(cur==NULL){
                Node* t = (Node*)malloc(sizeof(Node));
                t->value = tmp;
                t->nxt = NULL;
                p->nxt = t;
                break;
            }else{
                if(tmp%10>=cur->value%10){
                    p = cur;
                    cur = p->nxt;
                }else{
                    Node* t = (Node*)malloc(sizeof(Node));
                    t->value = tmp;
                    t->nxt = cur;
                    p->nxt = t;
                    break;
                }

            }
        }

    }


    int cnt = 0;
    for(int i=0;i<=bkn;i++){
        p=(lst+i)->nxt;
        while(p){
            arr[cnt]=p->value;
            cnt++;
            p = p->nxt;
        }
    }

    for(int i=0;i<=bkn;i++){
        p = lst + i;
        cur = p->nxt;
        p->nxt = NULL;
        while(cur){
            p = cur;
            cur = p->nxt;
            p->nxt = NULL;
            free(p);
        }
    }
    free(lst);

}
```

## 11. 基数排序

**ps : 以排序0~99为例**

### 11.1 算法流程

* 排序个位
* 在这个基础上排序十位，实现有序
* 对每一位的排序与[9.1](#9.1 算法流程)相同

### 11.1 C++代码

```c++
void radix_sort(int arr[], int n){

    int* cnt = (int*)malloc((10+2)*sizeof(int));
    int* tmp = (int*)malloc((n+2)*sizeof(int));
    for(int i=0;i<=10;i++) cnt[i]=0;

    for(int i=0;i<n;i++) cnt[arr[i]%10]++;
    for(int i=1;i<10;i++) cnt[i]+=cnt[i-1];

    for(int i=n-1;i>=0;i--) tmp[--cnt[arr[i]%10]]=arr[i];
    for(int i=0;i<n;i++) arr[i]=tmp[i];

    for(int i=0;i<=10;i++) cnt[i]=0;
    for(int i=0;i<n;i++) cnt[arr[i]/10]++;
    for(int i=1;i<10;i++) cnt[i]+=cnt[i-1];

    for(int i=n-1;i>=0;i--) tmp[--cnt[arr[i]/10]]=arr[i];
    for(int i=0;i<n;i++) arr[i]=tmp[i];

}
```

