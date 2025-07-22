# Sparse matrix

### Simple transpose

```c
  void simple_transpose(int sparse[][], int trans[][]){
    trans[0][0] = sparse[0][1];
    trans[0][1] = sparse[0][0];
    trans[0][2] = sparse[0][2];
    int t = sparse[0][2];
    int k = 1;
    for (int num=0;num<sparse[0][1];num++){
        for (int col=1;col<=t;col++){
            if(sparse[col][1]==num){
                trans[k][0]=sparse[col][1];
                trans[k][1]=sparse[col][0];
                trans[k][2]=sparse[col][2];
                k++;
            }
        }
    }
}
```
### Fast transpose

<img width="902" height="461" alt="image" src="https://github.com/user-attachments/assets/6e87057c-b5fd-4026-a6ee-30277edb441c" />


```c
void fast_transpose(int sparse[][], int trans[][]){
    int col=sparse[0][1];
    int total[col];
    int index[col+1];
    for(int i = 0; i<col; i++){total[i]=0;}
    for (int row_no=1;row_no<=sparse[0][2];row_no++){
        total[sparse[row_no][1]]++;
    }
    index[0]=1;
    for (int i=1;i<col;i++){
        index[i]=index[i-1]+total[i-1];
    }
    trans[0][0] = sparse[0][1];
    trans[0][1] = sparse[0][0];
    trans[0][2] = sparse[0][2];
    for(int j = 1; j<=sparse[0][2];j++){
        trans[index[sparse[j][1]]][0]=sparse[j][1];
        trans[index[sparse[j][1]]][1]=sparse[j][0];
        trans[index[sparse[j][1]]][2]=sparse[j][2];
        index[sparse[j][1]]++;
    }
}
```
