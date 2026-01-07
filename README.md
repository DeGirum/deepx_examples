
# **Using DeGirum PySDK, DeGirum Tools, and DEEPX Hardware**  

This repository provides a comprehensive guide on using **DeGirum PySDK**, **DeGirum Tools**, and **DEEPX hardware** for efficient AI inference. These tools simplify edge AI development by enabling seamless integration, testing, and deployment of AI models on **DEEPX M1A**.  

---

## **Table of Contents**  

1. [Introduction](#introduction)  
2. [Prerequisites](#prerequisites)  
3. [Setup](#setup)  
4. [Running and Configuring Jupyter Notebooks](#running-and-configuring-jupyter-notebooks) 
5. [Additional Resources](#additional-resources) 

---

## **1. Introduction**  

DeGirum provides a powerful suite of tools to simplify the development and deployment of edge AI applications:  

- [**DeGirum PySDK**](https://github.com/DeGirum/PySDKExamples): The core library for integrating AI inference capabilities into applications.  
- [**DeGirum Tools**](https://github.com/DeGirum/degirum_tools): Utilities for benchmarking, streaming, and interacting with DeGirum's model zoo.  

These tools are designed to be hardware-agnostic, enabling developers to build scalable, flexible solutions without being locked into a specific platform.  

---

## **2. Prerequisites**  

### **PySDK Requirements**

For complete DeGirum PySDK installation requirements (applicable for both cloud and local inference), see the [official documentation](https://docs.degirum.com/pysdk/installation)

### **For Running DEEPX Locally**

To run AI inference on DEEPX hardware locally, you also need:

1. **DEEPX Driver and Runtime**: Install the DEEPX driver and runtime on your system
2. **Runtime Version**: DeGirum PySDK supports DEEPX runtime version **2.95**

---

## **3. Setup**  

The best way to get started is to **clone this repository** and set up a virtual environment to keep dependencies organized. Follow these steps:  

### **Step 1: Clone the Repository**  
```bash
git clone https://github.com/DeGirum/deepx_examples.git
cd deepx_examples
```  

### **Step 2: Create a Virtual Environment**  
To keep the Python environment isolated, create a virtual environment:  

#### **Linux/macOS**  
```bash
python3 -m venv degirum_env
source degirum_env/bin/activate
```  

#### **Windows**  
```bash
python3 -m venv degirum_env
degirum_env\Scripts\activate
```  

### **Step 3: Install Required Dependencies**  
Install all necessary packages from `requirements.txt`:  

```bash
pip install -r requirements.txt
```  

---

### **Step 4: Add Virtual Environment to Jupyter**  

If you plan to use **Jupyter Notebooks**, ensure the virtual environment is available as a Jupyter kernel.  

#### **a) Activate the Virtual Environment (if not already active)**  
If you are not already inside the virtual environment, activate it:  

**Linux/macOS:**  
```bash
source degirum_env/bin/activate
```  

**Windows:**  
```bash
degirum_env\Scripts\activate
```  

#### **b) Ensure the Virtual Environment is Available in Jupyter**  
Since `notebook` and `ipykernel` are already installed via `requirements.txt`, simply run:  

```bash
python -m ipykernel install --user --name=degirum_env --display-name "Python (degirum_env)"
```  

This ensures that Jupyter recognizes the virtual environment as an available kernel.  

---

### **Step 5: Verify Installation**  

To confirm that DeGirum PySDK and all dependencies are properly installed, run the following command in your activated virtual environment:

```bash
python -c "import degirum; print(f'DeGirum PySDK version: {degirum.__version__}')"
```

If the installation was successful, you should see the version number of DeGirum PySDK printed to the console.

If you have a **local DEEPX hardware installation**, verify that the hardware is detected by running:

```bash
degirum sys-info
```

This command will display system information and list all available AI inference runtimes. Check the output to confirm that DEEPX is listed among the available runtimes.

---

### **Step 6: Setup DeGirum AI Hub Token (Optional)**  

If you plan to use **DeGirum AI Hub** for cloud-based inference, you will need to configure an authentication token. This token is **not required** for local inference.

For detailed instructions on how to obtain and manage your AI Hub tokens, please refer to the official documentation:  
👉 [**Managing AI Hub Tokens**](https://docs.degirum.com/pysdk/user-guide-pysdk/command-line-interface#manage-ai-hub-tokens)

---

## **4. Running and Configuring Jupyter Notebooks**  

This repository includes an `examples` folder containing multiple use case examples demonstrating how to run AI inference using DeGirum PySDK and DEEPX hardware. You can find detailed descriptions and usage instructions for each example in the [**Examples README**](examples/README.md).  

### **1. Start Jupyter Notebook**  
Now that the Jupyter environment is set up, you can start Jupyter Notebook:  

```bash
jupyter notebook
```  

This will open Jupyter in your web browser, allowing you to navigate to the `examples` folder and run the available notebooks.  

### **2. Ensure the Correct Kernel is Selected**  
When opening a notebook:  
- Go to **Kernel → Change Kernel**.  
- Select **Python (degirum_env)** to ensure the notebook runs inside the correct virtual environment.  


### **3. Default Notebook Settings and Customization**  
Each Jupyter Notebook in this repository is pre-configured with default inference settings, including the inference environment, model zoo location, and target hardware. However, you can modify these values if your setup requires different configurations.

Below are the default settings you will find in the notebooks, which you can adjust as needed:

#### **Select Inference Host Address**  
The `inference_host_address` determines where AI inference will be executed:  

```python
# Use local inference (e.g., when running on a device equipped with DEEPX M1A)
inference_host_address = "@local"

# Alternative: Specify a local server by IP or hostname
# inference_host_address = "localhost"

# Alternative: Use DeGirum AI Hub for cloud-based inference
# inference_host_address = "@cloud"
```  

#### **Choose Model Zoo Location**  
The `zoo_url` specifies where AI models are stored:  

```python
# Use DeGirum's cloud model zoo (recommended for DEEPX models)
zoo_url = "degirum/deepx"

# Alternative: Use a local directory containing models
# zoo_url = "../models"
```  


#### **Specify Target Hardware**  
The `device_type` defines the hardware used for inference:  

```python
# Default: DEEPX M1A device
device_type = "DEEPX/M1A"
```  
---
## **5. Additional Resources**

- **[DeGirum Documentation](https://docs.degirum.com/)** - Comprehensive guides and API references
- **[DeGirum Community](https://community.degirum.com/)** - Connect with other developers, ask questions, and share your projects
