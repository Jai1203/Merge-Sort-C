#include<stdio.h>
#include<stdlib.h>

void merge(int a[],int low,int mid,int high){
    int i=low;
    int j=mid+1;
    int k=low;
    int b[high+1];
    while(i<=mid&&j<=high){
        if(a[i]<a[j]){
            b[k]=a[i];
            i++;
            k++;
        }
        else{
            b[k]=a[j];
            j++;
            k++;
        }
    }
    while(i<=mid){
        b[k]=a[i];
        i++;
        k++;
    }
    while(j<=high){
        b[k]=a[j];
        j++;
        k++;
    }
    for(int i=low;i<=high;i++){
        a[i]=b[i];
    }
}

void mergesort(int a[],int low,int high){
    if(low<high){
        int mid=(low+high)/2;
        mergesort(a,low,mid);
        mergesort(a,mid+1,high);
        merge(a,low,mid,high);
    }
}

void printarr(int a[],int size){
    for(int i=0;i<size;i++){
        printf("%d ",a[i]);
    }
    printf("\n");
}

int main(){
    int a[]={99,1,34,56,77,87,3,2,4,5,86,54,34,68,93,53,23,12,8,9,10};
    int size=sizeof(a)/sizeof(a[0]);
    printf("original array is:");
    printarr(a,size);
    
    mergesort(a,0,size-1);
    
    printf("sorted array is:");
    printarr(a,size);
    return 0;
}
