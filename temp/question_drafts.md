[Back to Main](index.html)

Draft 1. Mean, Median, Mode

For self-test section, just try to use only <stdio.h> and don't use any other library

Let say if we have a long list of array (Just read [array section first](08_array_string.md)), for which we can find the mean,mode,median: 

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
    } 

Q2. Eigenvalues

### ~The real self tests (Written by Chan Chun Ping) ~Blame to this man

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

[Continue to The Next Page](06_rules_and_extra_features.html)

Q3. Conversions


### More Self-tests Question

One day, Starfall is feeling down as he is struggling to change to data type from string to other corrsponding data type (such as float,int more)so he asks his little buddy Ricky. Adrian once again replies to him that why don't you write your code.

```c
/*
Input: Array: The undesired array
       n    : The length of the array
*/
int stoi(char array[],int n) {

}

float stof(char array[],int n) {

}

bool stob(char array[],int n) {

}

int main() {
    char array1[] = "34";
    int n = sizeof(array1)/sizeof(array1[0]);
    cout << "The type of inputted array" +stoi(array1,n) + " and its repsective value is "+ stoi(array1,n) <<endl;

    char array2[] = "33.1";
    int n = sizeof(array2)/sizeof(array2[0]);
    cout << "The type of inputted array" +stoi(array2,n) + " and its repsective value is "+ stoi(array2,n) <<endl;

    bool array3[] = "T";
    int n = sizeof(array3)/sizeof(array3[0]);
    cout << "The type of inputted array" +stoi(array3,n) + " and its repsective value is "+ stoi(array3,n) <<endl;

}

```

Q4. Robots

One day, our poor software memeber Starfall have no idea how to make a state machine for a robot and he is clueless and once again, he ask his little buddy Ricky. Ricky replies that 
(I run out of things to say).
Here is the question: Imagine that you have Starfall in arbitary position in a 2D array matrix. We want to follow the boundary regardless the shape of the array

```c

#define NUM_ROW 10
#define NUM_COL 10

void moving(char array[][NUM_COL]) { //just using struct to make movement
        // If nothing, go South
        // If the bottom cell is blocked, go West
        // If the left cell is blocked, go North
        // If the top cell is blocked, go East
        // If the right cell is blocked, go South
        // If we reach the R spot, we need to output a message, saying that we have capture the reward

}

int main() {
    char array[NUM_ROW][NUM_COL] = {
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."S","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","-",
        "-","-","-","-","-"."-","-","-","-","R",
        }
    moving(array); 
}

```