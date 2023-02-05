import numpy as np
import pandas as pd

def detect_fraud(data):
    # calculate mean and standard deviation of data
    data_mean = np.mean(data)
    data_std = np.std(data)

    # set threshold for suspicious transactions
    threshold = data_mean + 3 * data_std

    # create a mask for transactions above threshold
    fraud_mask = data > threshold

    # return indices of fraud transactions
    return np.where(fraud_mask)

# example usage
data = pd.read_csv("transactions.csv")["amount"]
fraud_indices = detect_fraud(data)
print("Fraudulent transactions:", fraud_indices)
