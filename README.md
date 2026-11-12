# Ex-07-Spectral-Analysis-Spectral-Density-and-Time-Invariant-Linear-Filters
## NAME : Paladugu Venkata Balaji
## REG NO : 23050001005
## Aim
To perform spectral analysis on a simulated time series, identify dominant frequencies using a periodogram, apply a moving-average filter, and compare the spectral density before and after filtering.

## Objectives
1. To generate a time series containing multiple frequencies and random noise.
2. To calculate and plot the periodogram.
3. To identify the dominant frequency in the time series.
4. To apply a moving-average linear filter.
5. To compare the original and filtered time series.
5. To study the effect of changing the signal frequency, filter window size, and noise.
6. To observe the effect of adding another frequency component.
## Program
~~~python 
import numpy as np
import matplotlib.pyplot as plt
from scipy import signal
n = 500
t = np.arange(n)
np.random.seed(42)

x = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

plt.figure(figsize=(10, 4))
plt.plot(t, x)
plt.title("Original Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.grid(True)
plt.show()
frequency, power = signal.periodogram(x)

plt.figure(figsize=(10, 4))
plt.plot(frequency, power)
plt.title("Spectral Density of Original Time Series")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()
peak_index = np.argmax(power[1:]) + 1
dominant_frequency = frequency[peak_index]

print("Dominant Frequency:", dominant_frequency)
window = 5
filtered = np.convolve(
    x, np.ones(window) / window, mode="same"
)
plt.figure(figsize=(10, 4))
plt.plot(t, x, label="Original")
plt.plot(t, filtered, label="Filtered")
plt.title("Original vs Filtered Time Series")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.grid(True)
plt.show()
f_original, p_original = signal.periodogram(x)
f_filtered, p_filtered = signal.periodogram(filtered)

plt.figure(figsize=(10, 4))
plt.plot(f_original, p_original, label="Original")
plt.plot(f_filtered, p_filtered, label="Filtered")
plt.title("Spectral Density Before and After Filtering")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.legend()
plt.grid(True)
plt.show()
x_task1 = (
    np.sin(2 * np.pi * 0.10 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.random.randn(n)
)

f_task1, p_task1 = signal.periodogram(x_task1)

plt.figure(figsize=(10, 4))
plt.plot(f_task1, p_task1)
plt.title("Task 1: Effect of Changing Frequency")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()
window = 10
filtered_task2 = np.convolve(
    x, np.ones(window) / window, mode="same"
)

plt.figure(figsize=(10, 4))
plt.plot(t, x, label="Original")
plt.plot(t, filtered_task2, label="Filtered (Window = 10)")
plt.title("Task 2: Effect of Increasing Filter Window")
plt.xlabel("Time")
plt.ylabel("Value")
plt.legend()
plt.grid(True)
plt.show()
x_task3 = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
)

f_task3, p_task3 = signal.periodogram(x_task3)

plt.figure(figsize=(10, 4))
plt.plot(f_task3, p_task3)
plt.title("Task 3: Spectral Density Without Noise")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()
x_task4 = (
    np.sin(2 * np.pi * 0.05 * t)
    + 0.5 * np.sin(2 * np.pi * 0.20 * t)
    + 0.3 * np.sin(2 * np.pi * 0.30 * t)
    + 0.3 * np.random.randn(n)
)

f_task4, p_task4 = signal.periodogram(x_task4)

plt.figure(figsize=(10, 4))
plt.plot(f_task4, p_task4)
plt.title("Task 4: Spectral Density with an Additional Frequency")
plt.xlabel("Frequency")
plt.ylabel("Power")
plt.grid(True)
plt.show()

~~~

## Output
<img width="1052" height="505" alt="image" src="https://github.com/user-attachments/assets/262d112a-f155-41d1-b015-5ad3a86ef2c5" />
<img width="1081" height="488" alt="image" src="https://github.com/user-attachments/assets/24f81e85-67db-4be3-bce5-57a5fbf32509" />
<img width="1077" height="527" alt="image" src="https://github.com/user-attachments/assets/a0cd6ff7-a228-44d5-bcc6-0433c8de7186" />
<img width="1082" height="497" alt="image" src="https://github.com/user-attachments/assets/a6c52e4b-3343-4ee2-9584-be33876397c8" />
<img width="1085" height="461" alt="image" src="https://github.com/user-attachments/assets/b476def0-d714-45de-8cc3-01740955f06a" />
<img width="1082" height="476" alt="image" src="https://github.com/user-attachments/assets/e35bf6be-cb22-4f5a-b326-5923174231f6" />
<img width="1088" height="482" alt="image" src="https://github.com/user-attachments/assets/b3f17798-d869-4977-a978-f787668442b1" />
<img width="1070" height="482" alt="image" src="https://github.com/user-attachments/assets/a221c71b-e6f3-4b6d-8708-c74a2acdd5cf" />

## Result
Spectral analysis was performed successfully using the periodogram to identify dominant frequencies. A moving-average filter was applied to smooth the time series, and the spectral density before and after filtering was compared. The effects of changing frequency, removing noise, increasing the filter window, and adding another frequency component were studied.




