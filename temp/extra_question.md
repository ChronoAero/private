# Extra self-tests questions 
Written by Starfall 


For self-test section, just try to use only <stdio.h> and don't use any other library

Let say if we have a long list of array (Just read [array section first](08_array_string.md)), for which we can find the mean,mode,median,S.D.: 

    /* 
    Input: 
        array: Self-explantary
        n: Length of the array

    Output:
        mean: The mean of the array
    */
    float finding_mean(int array[],int n) { 

        return mean; 
    }

    /* 
    Input: 
        array: Self-explantary
        n: Length of the array

    Output:
        Mode: The Mode of the array

    Caution: 
        If there are more than one mode, we want it to be 
        
    */
    float finding_mode(int array[],int n){

    }

    /* 
    Input: 
        array: Self-explantary
        n: Length of the array

    Output:
        Median: The median of the array
    */
    float finding_median(int array[],int n) {

    }

    /* 
    Input: 
        array: Self-explantary
        n: Length of the array

    Output:
        S.D.: The S.D. of the array
    */
    float finding_sd(int array[],int n) {

    }

    /* 
    Input: 
        array: Self-explantary
        n: Length of the array

    Output:
        Array: The sorted array is sorted from smallest to biggest

    Remarks:
    Just a helper function, you don't need to do it if you don't want
    */
    int* BubbleSort(int array[],int n) { 

        
        return n
    }

    int main() { 
        int array[] = {3,4,5,6,1,2,3};
        int n = sizeof(array)/ sizeof(array[0]);
        cout << finding_mean(array,n) <<endl;
        cout << finding_median(array,n)<<endl;
        cout << finding_mode(array,n) <<endl;
        cout << finding_sd(array,n) <<endl; 

    } 


Extra question 2: 


Let say, One day Starfall is struggling with his Math 2111 homework. He is desperate to seek help from his buddy - Ricky. Ricky replies why don't you try to code it.

It is about eigen-values and eigen-vector. To make it simpler, we keep it to a 3x3 matrix. 

![Some example calucation for finding eigen-values](/images/Eigen-values.jpg)
()

If you don't get it, please look at the example: [Here](https://math.libretexts.org/Bookshelves/Linear_Algebra/A_First_Course_in_Linear_Algebra_(Kuttler)/07%3A_Spectral_Theory/7.01%3A_Eigenvalues_and_Eigenvectors_of_a_Matrix)

```c
#include <stdio.h>

#define MATRIX_SIZE 3

// Function to compute the eigenvalues and eigenvectors of a matrix
void compute_eigenvalues_eigenvectors(double matrix[MATRIX_SIZE][MATRIX_SIZE], double eigenvalues[MATRIX_SIZE], double eigenvectors[MATRIX_SIZE][MATRIX_SIZE]) {

}

int main() {
    // Example matrix
    double matrix[MATRIX_SIZE][MATRIX_SIZE] = {
        {1, 2, 3},
        {4, 5, 6},
        {7, 8, 10}
    };

    double eigenvalues[MATRIX_SIZE];
    double eigenvectors[MATRIX_SIZE][MATRIX_SIZE];

    compute_eigenvalues_eigenvectors(matrix, eigenvalues, eigenvectors);

    // Print the results
    printf("Eigenvalues:\n");
    for (int i = 0; i < MATRIX_SIZE; i++) {
        printf("%f\n", eigenvalues[i]);
    }

    printf("\nEigenvectors:\n");
    for (int i = 0; i < MATRIX_SIZE; i++) {
        for (int j = 0; j < MATRIX_SIZE; j++) {
            printf("%f ", eigenvectors[j][i]);
        }
        printf("\n");
    }

    return 0;
}


```

