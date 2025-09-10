import numpy as np

def input_matrix(name):
    print(f"\nEnter details for {name}:")
    rows = int(input("Enter number of rows: "))
    cols = int(input("Enter number of columns: "))
    print(f"Enter the elements row-wise (space separated):")
    elements = []
    for i in range(rows):
        row = list(map(float, input(f"Row {i+1}: ").strip().split()))
        while len(row) != cols:
            print(f"Please enter exactly {cols} elements.")
            row = list(map(float, input(f"Row {i+1}: ").strip().split()))
        elements.append(row)
    return np.array(elements)

def display_matrix(matrix):
    print("\nResultant Matrix:")
    print(matrix)

def matrix_addition(A, B):
    return A + B

def matrix_subtraction(A, B):
    return A - B

def matrix_multiplication(A, B):
    return np.dot(A, B)

def matrix_transpose(A):
    return A.T

def matrix_determinant(A):
    return np.linalg.det(A)

def main():
    print("===== Matrix Operations Tool =====")
    while True:
        print("\nAvailable Operations:")
        print("1. Addition")
        print("2. Subtraction")
        print("3. Multiplication")
        print("4. Transpose")
        print("5. Determinant")

        
        choice = input("Select an option (1-5): ")
        
        if choice == '1':
            A = input_matrix("Matrix A")
            B = input_matrix("Matrix B")
            if A.shape != B.shape:
                print("Error: Matrices must have the same dimensions for addition.")
            else:
                result = matrix_addition(A, B)
                display_matrix(result)
        
        elif choice == '2':
            A = input_matrix("Matrix A")
            B = input_matrix("Matrix B")
            if A.shape != B.shape:
                print("Error: Matrices must have the same dimensions for subtraction.")
            else:
                result = matrix_subtraction(A, B)
                display_matrix(result)
        
        elif choice == '3':
            A = input_matrix("Matrix A")
            B = input_matrix("Matrix B")
            if A.shape[1] != B.shape[0]:
                print("Error: Number of columns in A must equal number of rows in B for multiplication.")
            else:
                result = matrix_multiplication(A, B)
                display_matrix(result)
        
        elif choice == '4':
            A = input_matrix("Matrix A")
            result = matrix_transpose(A)
            display_matrix(result)
        
        elif choice == '5':
            A = input_matrix("Matrix A")
            if A.shape[0] != A.shape[1]:
                print("Error: Determinant can only be calculated for square matrices.")
            else:
                result = matrix_determinant(A)
                print(f"\nDeterminant of the matrix is: {result}")
        
        else:
            print("Invalid choice. Please select between 1 to 5.")

if __name__ == "__main__":
    main()
