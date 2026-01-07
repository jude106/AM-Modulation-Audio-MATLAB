# Audio Amplitude Modulation & Demodulation (MATLAB)

## 📌 Project Overview
This project is a complete MATLAB implementation of **Standard Amplitude Modulation (DSB-LC)** and **Demodulation** for real audio signals. Unlike simple simulations using sine waves, this system processes recorded audio files (`.wav`/`.mp3`), encoding them onto a high-frequency carrier and successfully recovering them using **Envelope Detection**.

Developed as part of the **Communication Systems 1** course at **Notre Dame University (NDU)**.

## 🚀 Key Features
* **Real-Audio Processing:** Automatically converts stereo audio to mono and normalizes signals to the `[-1, 1]` range.
* **User-Configurable Parameters:** Allows dynamic selection of Carrier Frequency ($f_c$), Carrier Amplitude ($A_c$), and Amplitude Sensitivity ($K_a$).
* **Robust Error Handling:** Includes built-in constraints to prevent **over-modulation** ($K_a > 1$) and aliasing.
* **Advanced Demodulation:** Uses a Diode Rectifier simulation followed by a **100-tap FIR Low-Pass Filter** to extract the message envelope with high precision.
* **Spectral Analysis:** Performs FFT analysis to visualize sidebands and carrier spikes in the frequency domain.

## 🛠️ Technical Implementation

### 1. Modulation (Transmitter)
The system generates the AM signal using the standard equation:
$$S(t) = A_c [1 + K_a \cdot m(t)] \cos(2\pi f_c t)$$
* **Sampling:** Utilizes the audio file's native sampling rate to avoid distortion.
* **Constraints:** Enforces $0 < K_a < 1$ to ensure a distortion-free envelope.

### 2. Demodulation (Receiver)
The project implements **Envelope Detection**, the classic method for AM recovery.
1.  **Rectification:** Takes the absolute value $|S(t)|$ to simulate a diode.
2.  **Low-Pass Filtering:** Applies a **linear-phase FIR filter** (Order: 100, Cutoff: ~5 kHz) using `filtfilt` to remove carrier harmonics without phase distortion.
3.  **DC Removal:** Subtracts the mean to recover the original AC audio signal.

## 📊 Visualizations
The code generates plots for every stage of the pipeline:
* **Time Domain:** Carrier, Message, and Modulated Signal.
* **Frequency Domain:** FFT plots showing the carrier ($f_c$) and sidebands ($f_c \pm f_m$).
* **Recovery:** Comparison of the Original vs. Demodulated signal.

*(Note: See the `docs/` folder for the full project report containing detailed plot analysis.)*

## 💻 How to Run
1.  **Prerequisites:** MATLAB R2020 or newer (No extra toolboxes required).
2.  **Clone the Repo:**
    ```bash
    git clone [https://github.com/jude106/AM-Audio-Modulation.git](https://github.com/YOUR_USERNAME/AM-Audio-Modulation.git)
    ```
3.  **Run the Script:** Open `amplitude_modulation_audio.mlx` in MATLAB.
4.  **Input Parameters:** When prompted, enter values such as:
    * Carrier Frequency: `10000` Hz
    * Carrier Amplitude: `5`
    * Amplitude Sensitivity: `0.5`
5.  **Select Audio:** A file dialog will appear; select any `.wav` file on your computer.

## 👥 Authors
* **Jude Hobeiche**
* **Christopher El Sabbagh**

## 📄 License
This project is for educational purposes demonstrating analog communication principles.
