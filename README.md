# Audio Amplitude Modulation & Demodulation (MATLAB)

## 📌 Project Overview
[cite_start]This project is a complete MATLAB implementation of **Standard Amplitude Modulation (DSB-LC)** and **Demodulation** for real audio signals[cite: 109, 111]. [cite_start]Unlike simple simulations using sine waves, this system processes recorded audio files (`.wav`/`.mp3`), encoding them onto a high-frequency carrier and successfully recovering them using **Envelope Detection**[cite: 120, 123].

[cite_start]Developed as part of the **Communication Systems 1** course at **Notre Dame University (NDU)**[cite: 79, 84].

## 🚀 Key Features
* [cite_start]**Real-Audio Processing:** automatically converts stereo audio to mono and normalizes signals to the `[-1, 1]` range[cite: 257, 258].
* [cite_start]**User-Configurable Parameters:** Allows dynamic selection of Carrier Frequency ($f_c$), Carrier Amplitude ($A_c$), and Amplitude Sensitivity ($K_a$) [cite: 231-234].
* [cite_start]**Robust Error Handling:** Includes built-in constraints to prevent **over-modulation** ($K_a > 1$) and aliasing[cite: 129, 239].
* [cite_start]**Advanced Demodulation:** Uses a Diode Rectifier simulation followed by a **100-tap FIR Low-Pass Filter** to extract the message envelope with high precision[cite: 363].
* [cite_start]**Spectral Analysis:** Performs FFT analysis to visualize sidebands and carrier spikes in the frequency domain[cite: 286].

## 🛠️ Technical Implementation

### 1. Modulation (Transmitter)
[cite_start]The system generates the AM signal using the standard equation[cite: 203]:
$$S(t) = A_c [1 + K_a \cdot m(t)] \cos(2\pi f_c t)$$
* [cite_start]**Sampling:** Utilizes the audio file's native sampling rate to avoid distortion[cite: 175].
* [cite_start]**Constraints:** Enforces $0 < K_a < 1$ to ensure a distortion-free envelope[cite: 129].

### 2. Demodulation (Receiver)
[cite_start]The project implements **Envelope Detection**, the classic method for AM recovery[cite: 336].
1.  [cite_start]**Rectification:** Takes the absolute value $|S(t)|$ to simulate a diode[cite: 340].
2.  [cite_start]**Low-Pass Filtering:** Applies a **linear-phase FIR filter** (Order: 100, Cutoff: ~5 kHz) using `filtfilt` to remove carrier harmonics without phase distortion[cite: 362, 363, 365].
3.  [cite_start]**DC Removal:** Subtracts the mean to recover the original AC audio signal[cite: 387].

## 📊 Visualizations
The code generates plots for every stage of the pipeline:
* [cite_start]**Time Domain:** Carrier, Message, and Modulated Signal[cite: 125].
* [cite_start]**Frequency Domain:** FFT plots showing the carrier ($f_c$) and sidebands ($f_c \pm f_m$)[cite: 209, 292].
* **Recovery:** Comparison of the Original vs. Demodulated signal.

*(Note: See the `docs/` folder for the full project report containing detailed plot analysis.)*

## 💻 How to Run
1.  [cite_start]**Prerequisites:** MATLAB R2020 or newer (No extra toolboxes required)[cite: 427, 428].
2.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/YOUR_USERNAME/AM-Audio-Modulation.git](https://github.com/YOUR_USERNAME/AM-Audio-Modulation.git)
    ```
3.  **Run the Script:** Open `amplitude_modulation_audio.mlx` in MATLAB.
4.  **Input Parameters:** When prompted, enter values such as:
    * Carrier Frequency: `10000` Hz
    * Carrier Amplitude: `5`
    * [cite_start]Amplitude Sensitivity: `0.5` [cite: 133-135].
5.  **Select Audio:** A file dialog will appear; select any `.wav` file on your computer.

## 👥 Authors
* [cite_start]**Jude Hobeiche** [cite: 86]
* [cite_start]**Christopher El Sabbagh** [cite: 87]

## 📄 License
This project is for educational purposes demonstrating analog communication principles.
