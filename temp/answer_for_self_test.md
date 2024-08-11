### Answers for self-tests (Written by Starfall)

For operators one(Matrix_calucation):

```c
// Function to compute the eigenvalues and eigenvectors of a matrix
void compute_eigenvalues_eigenvectors(double matrix[MATRIX_SIZE][MATRIX_SIZE], double eigenvalues[MATRIX_SIZE], double eigenvectors[MATRIX_SIZE][MATRIX_SIZE]) {

    double characteristic_polynomial[MATRIX_SIZE + 1];
    double temp_matrix[MATRIX_SIZE][MATRIX_SIZE];

    // Compute the characteristic polynomial of the matrix
    characteristic_polynomial[MATRIX_SIZE] = 1;
    for (int i = 0; i < MATRIX_SIZE; i++) {
        characteristic_polynomial[i] = -matrix[i][i];
        for (int j = 0; j < MATRIX_SIZE; j++) {
            if (i != j) {
                characteristic_polynomial[i] -= matrix[i][j] * matrix[j][i];
            }
        }
    }

    // Find the roots of the characteristic polynomial (eigenvalues)
    for (int i = 0; i < MATRIX_SIZE; i++) {
        double a = characteristic_polynomial[i + 1];
        double b = characteristic_polynomial[i];
        double discriminant = b * b - 4 * a;
        if (discriminant >= 0) {
            eigenvalues[i] = (-b + sqrt(b * b - 4 * a)) / (2 * a);
        } else {
            eigenvalues[i] = (-b) / (2 * a);
        }
    }

    // Compute the eigenvectors
    for (int i = 0; i < MATRIX_SIZE; i++) {
        for (int j = 0; j < MATRIX_SIZE; j++) {
            temp_matrix[j][j] = matrix[j][j] - eigenvalues[i];
        }
        for (int j = 0; j < MATRIX_SIZE; j++) {
            for (int k = 0; k < MATRIX_SIZE; k++) {
                if (j != k) {
                    temp_matrix[j][k] = matrix[j][k];
                }
            }
        }
        double determinant = temp_matrix[0][0] * (temp_matrix[1][1] * temp_matrix[2][2] - temp_matrix[1][2] * temp_matrix[2][1]) -
                                temp_matrix[0][1] * (temp_matrix[1][0] * temp_matrix[2][2] - temp_matrix[1][2] * temp_matrix[2][0]) +
                                temp_matrix[0][2] * (temp_matrix[1][0] * temp_matrix[2][1] - temp_matrix[1][1] * temp_matrix[2][0]);
        if (fabs(determinant) > 1e-10) {
            eigenvectors[0][i] = (temp_matrix[1][1] * temp_matrix[2][2] - temp_matrix[1][2] * temp_matrix[2][1]) / determinant;
            eigenvectors[1][i] = -(temp_matrix[0][1] * temp_matrix[2][2] - temp_matrix[0][2] * temp_matrix[2][1]) / determinant;
            eigenvectors[2][i] = (temp_matrix[0][1] * temp_matrix[1][2] - temp_matrix[0][2] * temp_matrix[1][1]) / determinant;
        } else {
            eigenvectors[0][i] = 1;
            eigenvectors[1][i] = 0;
            eigenvectors[2][i] = 0;
        }
    }
}

```

