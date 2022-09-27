# pointer-using
delete same number and delete if there are '5' and change array that small number is first
# c
#include <stdio.h> #include <stdlib.h>   
void remove_element(int *d,int j,int *n); void remove_duplicate(int *d,int *n); void remove_5(int *d,int *n); void bsort_a(int *d,int n);
void main(){
	int D[10],i,N=10;
	srand(4);
	for(i=0;i<10;i++) D[i]=rand()%100;
	printf("Before: ");
	for(i=0;i<10;i++) printf("%d  ",D[i]); puts("");
	remove_duplicate(D,&N); printf("remove_d:"); 
	for(i=0;i<N;i++) { printf(" %d",D[i]);} printf("\n");
	remove_5(D,&N); printf("remove_5:"); for(i=0;i<N;i++) printf(" %d",D[i]);
	printf("\n"); bsort_a(D,N);
	printf("After: ");
	for(i=0;i<N;i++) printf("%d  ",D[i]); puts("");
}
void remove_element(int *d,int j,int *n){
	int i;
	for(i=j;i<*n;i++){
		*(d+i)=*(d+i+1);
	}
	*(d+*n-1)=0;
	*n= *n-1;
}
void remove_duplicate(int *d,int *n){
	int i,j;
	for(i=0;i<*n-1;i++){
		for(j=i+1;j<*n;j++){
			if(d[i]==d[j]){
				remove_element(d,j,n);
				j--;
			}
		}
	}
}
void remove_5(int *d,int *n){
	int x,y;
	for(y=0;y<*n;y++){
		if((*(d+y)%5==0) || (*(d+y)%10==5) || (*(d+y)/10==5)){
			for(x=y; x<*n-1;x++){
				*(d+x)=*(d+x+1);
			}
			*(d+x+1) = 0;
			*n= *n-1;
			y-=1;
		}
	}
}
void bsort_a(int *d,int n){
	int i,j;
	for(i=0;i<n-1;i++){
		for(j=0;j<n-i-1;j++){
			if(*(d+j)>*(d+j+1)){
				int tmp=*(d+j);
				*(d+j)=*(d+j+1);
				*(d+j+1)=tmp;
			}
		}
	}
}
