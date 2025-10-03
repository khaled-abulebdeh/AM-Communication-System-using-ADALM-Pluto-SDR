# AM Communication System using ADALM-Pluto SDR

## Project Overview

This repository contains the files for a university course project focused on the design and implementation of a **Normal Amplitude Modulation (AM)** communication system. The system utilizes **Software-Defined Radio (SDR)** principles, specifically the **Analog Devices ADALM-Pluto** device, to transmit and receive both **monotone (single-tone)** and **audio signals** in real-time.

The core implementation is achieved through modular flowgraphs in **GNU Radio Companion (GRC)**, providing a practical, hands-on demonstration of fundamental modulation and demodulation concepts.

## Features

* **Normal AM (Full-Carrier) Implementation:** Complete flowgraphs for both modulation (transmission) and non-coherent demodulation (reception).
* **Real-time SDR Transmission:** Utilizes the **ADALM-Pluto** device for over-the-air signal transmission.
* **Signal Support:** Capable of transmitting and receiving a pure **monotone signal** (e.g., 1 kHz sine wave) and **audio input**.
* **GNU Radio Companion (GRC) Files:** Includes the editable `.grc` files for easy parameter tuning and visualization of the system at various stages (time domain and frequency domain).

## Technologies and Prerequisites

To successfully run this project, you will need the following hardware and software installed:

| Component | Type | Requirement |
| :--- | :--- | :--- |
| **Software** | GNU Radio | Version 3.8+ recommended |
| **Software** | OS Support | Linux (preferred) or Windows/macOS |
| **GNU Radio Blocks** | `gr-iio` | Required for ADALM-Pluto (PlutoSDR Sink/Source blocks) |
| **Hardware** | ADALM-Pluto SDR | One device for the full loopback system |

### Installation and Setup

1.  **Install GNU Radio:** Follow the official instructions to install GNU Radio for your operating system.
2.  **Install `gr-iio`:** This package provides the necessary Source and Sink blocks to interface with the ADALM-Pluto.
    ```bash
    # Example for Linux (adjust based on your distribution)
    sudo apt install gnuradio-iio
    ```
3.  **Connect ADALM-Pluto:** Ensure your ADALM-Pluto is connected to your computer and its firmware is up-to-date. It should be recognized by your system (often as a network adapter).

## Usage

The project consists of three main GNU Radio Companion files (`.grc`).

### 1. The Transmitter (`modulation.grc`)

This flowgraph is responsible for generating the message signal (monotone or audio), modulating it onto a carrier wave using **Normal AM**, and transmitting the complex baseband signal via the ADALM-Pluto.

1.  Open `modulation.grc` in GNU Radio Companion.
2.  Review the blocks, especially the signal source (for monotone) or an audio source (if used).
3.  Verify the carrier frequency and sample rate variables.
4.  Run the flowgraph (**F6** or the **Run** button). The Pluto will begin transmitting the signal.

### 2. The Receiver (`demodulation.grc`)

This flowgraph is the full receiver chain. It receives the signal from the Pluto, applies the non-coherent AM demodulation technique, filters the resulting audio, and plays the recovered signal through the computer's audio output.

1.  Open `demodulation.grc` in GNU Radio Companion.
2.  Verify the input frequency and sample rate match the transmitter settings.
3.  Ensure the **Audio Sink** block is correctly configured for your system's audio output.
4.  Run the flowgraph (**F6** or the **Run** button).

### 3. Audio Test Flowgraph (`sound.grc`)

This flowgraph appears to be a separate or intermediate flowgraph related to audio signal processing, likely used for testing audio resamplers or filter chains prior to the main AM implementation. It is included for reference and testing purposes.

1.  Open `sound.grc` to test the audio signal flow and ensure proper sample rate conversion between audio devices and the SDR flowgraphs.

