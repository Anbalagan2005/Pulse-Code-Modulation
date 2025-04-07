# Pulse-Code-Modulation
# Aim:
To implement and analyze the Pulse Code Modulation (PCM) process using Python by
performing sampling, quantization, and encoding of an analog signal.
# Tools required:
IDE python with scipy and numpy
# Program:
```
import matplotlib.pyplot as plt
import numpy as np

# Parameters
sampling_rate = 5000               # Samples per second
frequency = 50                     # Frequency of the analog message signal
duration = 0.1                     # Duration in seconds
quantization_levels = 16           # PCM quantization levels (resolution)

# Generate time vector
t = np.linspace(0, duration, int(sampling_rate * duration), endpoint=False)

# Generate message signal (analog signal)
message_signal = np.sin(2 * np.pi * frequency * t)

# Generate clock signal (sampling clock) with increased frequency
clock_signal = np.sign(np.sin(2 * np.pi * 200 * t))  # 200 Hz clock signal

# Quantize the message signal
quantization_step = (max(message_signal) - min(message_signal)) / quantization_levels
quantized_signal = np.round((message_signal - min(message_signal)) / quantization_step) * quantization_step + min(message_signal)

# Simulate PCM signal (as integer level values)
pcm_signal = ((quantized_signal - min(quantized_signal)) / quantization_step).astype(int)

# Plotting the results
plt.figure(figsize=(12, 10))

# Plot message signal
plt.subplot(4, 1, 1)
plt.plot(t, message_signal, label="Message Signal (Analog)", color='blue')
plt.title("Message Signal (Analog)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot clock signal
plt.subplot(4, 1, 2)
plt.plot(t, clock_signal, label="Clock Signal (200 Hz)", color='green')
plt.title("Clock Signal (Increased Frequency)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot quantized signal (PCM modulated)
plt.subplot(4, 1, 3)
plt.step(t, quantized_signal, label="PCM Modulated Signal", color='red', where='mid')
plt.title("PCM Modulated Signal (Quantized)")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

# Plot PCM demodulation (for visualization purposes, this is same as quantized)
plt.subplot(4, 1, 4)
plt.plot(t, quantized_signal, label="Signal Demodulation", color='purple', linestyle='--')
plt.title("Signal Without Demodulation")
plt.xlabel("Time [s]")
plt.ylabel("Amplitude")
plt.grid(True)

plt.tight_layout()
plt.show()
```

# Output Waveform:
![image](https://github.com/user-attachments/assets/b6b5cdee-eafe-4b7c-8687-9bc4ae2ed5cb)

# Result:
Thus, an analog signal is successfully digitized using Pulse Code Modulation (PCM) in
Python.
