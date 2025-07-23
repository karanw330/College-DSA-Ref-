# Sorting Algorithms
### 1. Bubble Sort
```c
void bubble(int arr[], int arrsize){
    for (int i = 0; i < arrsize - 1; i++){
        for (int j = 0; j < arrsize - i - 1; j++){
            if (arr[j] > arr[j + 1]){
                int temp = arr[j];
                arr[j] = arr[j + 1];
                arr[j + 1] = temp;
            }
        }
    }
}
```
### 2. Selection sort
```c
void selection(int arr[], int arrsize){
    for (int i = 0; i < arrsize - 1; i++){
        int min = i;
        for (int j = i + 1; j < arrsize; j++){
            if (arr[j] < arr[min]){
                min = j;
            }
        }
        if (min != i){
            int temp = arr[i];
            arr[i] = arr[min];
            arr[min] = temp;
        }
    }
}
```
### Insertion sort
```c
void insertion(int arr[], int arrsize){
    for (int i = 1; i < arrsize; i++){
        int key = arr[i];
        int j = i - 1;
        while (j >= 0 && arr[j] > key){
            arr[j + 1] = arr[j];
            j--;
        }
        arr[j + 1] = key;
    }
}
```
