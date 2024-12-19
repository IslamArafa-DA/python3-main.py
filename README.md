                  ## Final outlet for programming Numpy Array
import numpy as np
###create function to calculate  statistics for 9 numbers as a matrix
def calculate(numbers):
    if len(numbers) != 9:
        raise ValueError("List must contain nine numbers.")
    
    array = np.array(numbers).reshape(3, 3) ### convert list to numpy array
    #### Calculation as dictionary and values to list , for array rows, columns and flattened
    calculations = {
        'mean': [
            np.round(array.mean(axis=0),2).tolist(),
            np.round(array.mean(axis=1),2).tolist(),
            np.round(array.mean(),2).tolist()
        ],
        'variance': [
            np.round(array.var(axis=0),2).tolist(),
            np.round(array.var(axis=1),2).tolist(),
            np.round(array.var(),2).tolist()
        ],
        'std_dev': [
            np.round(array.std(axis=0),2).tolist(),
            np.round(array.std(axis=1),2).tolist(),
            np.round(array.std(),2).tolist()
        ],
        'max_values': [
            array.max(axis=0).tolist(),
            array.max(axis=1).tolist(),
            array.max().tolist()
        ],
        'min_values': [
            array.min(axis=0).tolist(),
            array.min(axis=1).tolist(),
            array.min().tolist()
        ],
        'sum_values': [
            array.sum(axis=0).tolist(),
            array.sum(axis=1).tolist(),
            array.sum().tolist()
        ]
    }
    return calculations


try:
    calculate_input = input("Please enter 9 digits to be calculated (separated by spaces): ")
    X = list(map(int, calculate_input.split()))
    calculations = calculate(X)
    result = "\n".join([f"{key}: {value}" for key, value in calculations.items()])
    print (result)


except ValueError as e:
    print(e)
