# eeg
eeg det
import mne
import numpy as np

# Generate synthetic EEG data
sfreq = 1000  # Sampling frequency (Hz)
times = np.arange(0, 10, 1/sfreq)  # 10 seconds of data
data = np.sin(2 * np.pi * 10 * times)  # 10 Hz sine wave as an example

# Create MNE Raw object
info = mne.create_info(ch_names=['EEG 1'], sfreq=sfreq, ch_types=['eeg'])
raw = mne.io.RawArray(data.reshape(1, -1), info)

# Plot the EEG data
raw.plot()

# Perform basic EEG analysis (e.g., power spectral density)
raw.plot_psd(fmax=50)
