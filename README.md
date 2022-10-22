# Data-structures---merge-sorting

#include<iostream>
using namespace std;
class sort
{
 public:
 int a[100],n;
 void get();
 void mergesort(int,int);
 void merge(int,int,int);
 void put();
};
void sort::get()
{
 cout<<"\nEnter n value:";
 cin>>n;
 cout<<"\nEnter "<<n<<" values:";
 for(int i=0;i<n;i++)
 {
 cin>>a[i];
 }
}
void sort::mergesort(int l,int h)
{
 int m;
 if(l<h)
 {
 m=(l+h)/2;
 mergesort(l,m);
 mergesort(m+1,h);
 merge(l,m,h);
 }
}
void sort::merge(int l,int m,int h)
{
 int i=l,j=m+1,k=l,t[100];
 while(i<=m && j<=h)
 {
 if(a[i]<a[j])
 {
 t[k++]=a[i++];
 }
 else
 {
 t[k++]=a[j++];
 }
 }
 if(i>m)
 {
 for(int s=j;s<=h;s++)
 {
 t[k++]=a[s];                               
 }
}

 else
 {
 for(int s=i;s<=m;s++)
 { 
 t[k++]=a[s];
 }
 }
 for(int b=l;b<=h;b++) 
 {
 a[b]=t[b];
 } 
}
void sort::put()
{
 cout<<"\nThe elements are...";
 for(int i=0;i<n;i++)
 {
 cout<<a[i]<<"\t";
 }
}
int main()
{
 sort ob;
 ob.get();
 ob.mergesort(0,(ob.n)-1);
 ob.put();
 return 0;
}
