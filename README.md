# AM Communication System using ADALM-Pluto SDR 📡

## Project Overview

This project focuses on the design and implementation of a **Normal Amplitude Modulation (AM)** communication system, utilizing the files within this repository. The system employs **Software-Defined Radio (SDR)** principles and the **Analog Devices ADALM-Pluto** device to transmit and receive both **monotone (single-tone)** and **audio signals** in real-time.

The core implementation is achieved through modular flowgraphs in **GNU Radio Companion (GRC)**, providing a practical, hands-on demonstration of fundamental modulation and demodulation concepts, as detailed in the accompanying project report.

## Features

* **Normal AM (Full-Carrier) Implementation:** Complete flowgraphs for both modulation (transmission) and non-coherent demodulation (reception).
* **Real-time SDR Transmission:** Utilizes the **ADALM-Pluto** device for over-the-air signal transmission.
* **Signal Support:** Capable of transmitting and receiving a pure **monotone signal** (e.g., 1 kHz sine wave) and **audio input**.
* **GNU Radio Companion (GRC) Files:** Includes the editable `.grc` files for easy parameter tuning and visualization of the system's spectral and time-domain characteristics.

***

## Technologies and Prerequisites

To successfully run this project, you will need the following hardware and software installed:

| Component | Type | Requirement |
| :--- | :--- | :--- |
| **Software** | **GNU Radio** | Version 3.8+ recommended |
| **GNU Radio Blocks** | **`gr-iio`** | Required for ADALM-Pluto (PlutoSDR Sink/Source blocks) |
| **Hardware** | **ADALM-Pluto SDR** | One device for the full loopback system |

### Installation and Setup

1.  **Install GNU Radio:** Follow the official instructions for your operating system.
2.  **Install `gr-iio`:** This package is essential for interfacing with the ADALM-Pluto.
    ```bash
    # Example command for Debian/Ubuntu-based systems
    sudo apt install gnuradio-iio
    ```
3.  **Connect ADALM-Pluto:** Ensure your ADALM-Pluto is connected and properly configured (e.g., recognized by your system).

***

## Usage: Running the Flowgraphs

The project is structured around three main GNU Radio Companion files (`.grc`).

### 1. The Transmitter (`modulation.grc`)

This flowgraph generates the message signal, performs **Normal AM modulation**, and transmits the signal via the ADALM-Pluto **SDR Sink**.

1.  Open `modulation.grc` in GNU Radio Companion.
2.  Review the variables for carrier frequency, sample rate, and signal source configuration.
3.  Run the flowgraph (**F6** or the **Run** button). The Pluto will begin transmission.

### 2. The Receiver (`demodulation.grc`)

This flowgraph is the complete receiver chain. It receives the signal via the ADALM-Pluto **SDR Source**, applies the **non-coherent AM demodulation** technique, filters the resulting audio, and plays the recovered signal through the **Audio Sink**.

1.  Open `demodulation.grc` in GNU Radio Companion.
2.  Verify the input frequency and sample rate match the transmitter settings.
3.  Run the flowgraph (**F6** or the **Run** button).

### 3. Audio Test Flowgraph (`sound.grc`)

This flowgraph is an auxiliary file for testing the audio signal chain and verifying proper sample rate conversion using the `rational_resampler` blocks, independent of the main AM system.

***
