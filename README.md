# External Merge Sort
#include<iostream>
using namespace std;
int main () {
	int* r;
	int size,buffer,i;
	cout << "Enter the number of the pages will be sorted: " << endl;
    cin>>size;
    cout << "The pages are: " << endl;
	for(i=0;i<size;i++)
	cin >>r[i];
	cout << "Enter the buffer size: " << endl;
	cin >>buffer;
	for(i=0;i<buffer;i++){
		heap(r,size);
		heapify(r,size,i);
	}
	
	
}
void heapify(int* r,int size, int i){
	int smallest=i;
	int left=2*i+1;
	int right=2*i+2;
	if(left<i && r[left]<r[i])
	smallest=left;
	if(right<i && r[right]<r[i])
	smallest=right;
	if(smallest!=i){
	swap(r[i],r[smallest]);
	heapify(r,size,i);}
}
void heap(int* r,int size){
	for(int i=size/2-1;i>=0;i--)
	heapify(r,size,i);
	for(int i=size-1;i>=0;i++){
		swap(r[0],r[i]);
		heapify(r,i,0);
	}
}
void swap(int* x,int* y){
	int shift=*x;
	*x=*y;
	*y=shift;
}
void mergesort(int* r,int l,int g){
	int m;
	if(l<g)
	m=(l+g)/2;
	mergesort(r,l,m);
	mergesort(r,m+1,g);
	merge(r,l,m,g);
}
void merge(int* r,int l,int m,int g){
	int n1=m-l+1;
	int n2=g-m;
	int* r1;
	int* r2;
	for(int i=0;i<n1;i++)
	r1[i]=r[l+i];
	for(int j=0;j<n2;j++)
	r2[j]=r[m+1+j];
	int i=0,j=0,k=1;
	while (i<n1&&j<n2){
		if(r1[i]<=r2[j]){
		r[k]=r1[i];
		k++;}
		else {
		r[k]=r2[j];
		j++;}
		k++;
	}
}
void print(int* r,int size){
	for(int i=0;i<size;i++)
	cout <<r[i];
}
