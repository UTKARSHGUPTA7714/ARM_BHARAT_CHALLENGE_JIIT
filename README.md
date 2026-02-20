# ARM_BHARAT_CHALLENGE_JIIT
Hardware-accelerated CNN on Xilinx Zynq FPGA -16.8× speedup over CPU
Real-Time CNN Inference on Xilinx Zynq FPGA with Arm Processor
Problem Statement 5 — Hardware-Accelerated CNN for Real-Time Object Detection/Image Classification on Xilinx Zynq SoC

📌 Project Overview
This project implements a hardware-accelerated Convolutional Neural Network (CNN) on a Xilinx Zynq SoC, combining the Arm Cortex-A9 processor with FPGA fabric for real-time MNIST digit classification. The system achieves a 16.8× speedup over a CPU-only (software) implementation.
The architecture follows a hardware/software co-design approach:
Arm Core: Image loading, preprocessing, control logic, and post-processing
FPGA Fabric: Accelerated CNN operations (convolution, pooling, activation) via AXI DMA
📁 Repository Structure
cnn_mnist__bharat_ar.../
├── app_model_bharat_ar.../        # Application model files
├── model_bharat_arm_ch.../        # Trained CNN model (.pt file)
├── rtl_pipelined_bharat_ar.../    # Pipelined RTL implementation (Vitis HLS / Vivado)
├── rtl_vanilla_bharat_ar.../      # Baseline (vanilla) RTL implementation
├── target_bharat_arm_ch.../       # Target bitstream and deployment files
└── compare_hw_vs_sw.ipynb         # Main Jupyter Notebook for HW vs SW comparison
🧠 CNN Architecture
A lightweight CNN trained on the MNIST dataset:
Layer
Details
Conv1
Input: (1×28×28) → Output: (3×24×24), kernel 5×5
MaxPool1
Output: (3×12×12)
Conv2
Input: (3×12×12) → Output: (3×8×8), kernel 5×5
MaxPool2
Output: (3×4×4)
Flatten
48 features
FC
48 → 10 (digit classes)
Output
log_softmax
⚡ Performance Results
Implementation
Inference Time
Speedup
Software (Arm CPU)
~15.29 ms
1× (baseline)
Hardware (FPGA)
~0.91 ms
16.8×
🛠️ Hardware & Tools
Platform: Xilinx Zynq SoC (e.g., PYNQ-Z1 / PYNQ-Z2)
HLS Tool: Vitis HLS / Vivado
Framework: PYNQ (pynq, AXI DMA)
ML Framework: PyTorch
Language: Python, C/C++ (HLS)
🚀 How to Run
Prerequisites
PYNQ board with Jupyter Notebook access
Python packages: torch, numpy, Pillow, matplotlib, pynq
Steps
Clone the repository onto your PYNQ board or local machine.
Place the trained model (cnn_mnist.pt) at /home/ubuntu/workspace/cnn_mnist.pt.
Place the bitstream (cnn_mnist.bit) at /home/ubuntu/workspace/cnn_mnist.bit.
Place sample images in /home/ubuntu/workspace/bmp/ (e.g., train_0.bmp).
Open compare_hw_vs_sw.ipynb in Jupyter Notebook.
Run all cells sequentially:
Section 1: Loads the CNN model
Section 2: Runs SW inference and measures time
Section 3: Programs the FPGA bitstream
Section 4: Runs HW inference via AXI DMA
Section 5: Prints the speedup factor
📊 Key Results
Running on a bitmap image of digit 5:
SW Predicted output: 5 ✅ (Time: ~15.3 ms)
HW Predicted output: 5 ✅ (Time: ~0.91 ms)
Hardware acceleration speedup: 16.8×
👥 Team
Team Name: Bharat Arm
Project: CNN MNIST — FPGA Hardware Acceleration
📄 License
This project was developed for academic purposes as part of an embedded systems / FPGA design course.
