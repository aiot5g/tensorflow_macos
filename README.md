## Mac-optimized TensorFlow and TensorFlow Addons

### INTRODUCTION

This pre-release delivers hardware-accelerated TensorFlow and TensorFlow Addons for macOS 11.0+.  Native hardware acceleration is supported on Macs with M1 and Intel-based Macs through Apple’s [ML Compute](https://developer.apple.com/documentation/mlcompute) framework.

### SUPPORTED VERSIONS

- TensorFlow r2.4rc0
- TensorFlow Addons 0.11.2

### REQUIREMENTS

- macOS 11.0+
- Python 3.8, available from the [Xcode Command Line Tools](https://developer.apple.com/download/more/?=command%20line%20tools)

### INSTALLATION

An archive containing Python packages and an installation script can be downloaded from the [releases](https://github.com/apple/tensorflow_macos/releases).

#### Details

- To quickly try this out, copy and paste the following into Terminal: 

  ``` 
  /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/apple/tensorflow_macos/master/scripts/download_and_install.sh)"
  ```
  This will verify your system, ask you for confirmation, then create a [virtual environment](https://docs.python.org/3.8/tutorial/venv.html) with TensorFlow for macOS installed.

- Alternatively, download the archive file from the [releases](https://github.com/apple/tensorflow_macos/releases).  The archive contains an installation script, 
  accelerated versions of TensorFlow, TensorFlow Addons, and needed dependencies.  

#### Notes

For Macs with M1, the following packages are currently unavailable:
- SciPy and dependent packages
- Server/Client TensorBoard packages

### ISSUES AND FEEDBACK

Feedback is welcomed!

Please submit feature requests or report issues via [GitHub Issues](https://github.com/apple/tensorflow_macos/issues).

### ADDITIONAL INFORMATION
    
#### Device Selection (Optional)

It is not necessary to make any changes to your existing TensorFlow scripts to use ML Compute as a backend for TensorFlow and TensorFlow Addons.

There is an optional `mlcompute.set_mlc_device(device_name=’any')` API for ML Compute device selection. The default value for `device_name` is `'any’`, which means ML Compute will select the best available device on your system, including multiple GPUs on multi-GPU configurations. Other available options are `‘cpu’` and `‘gpu’`. Please note that in eager mode, ML Compute will use the CPU. For example, to choose the CPU device, you may do the following:

    # Import mlcompute module to use the optional set_mlc_device API for device selection with ML Compute.
    from tensorflow.python.compiler.mlcompute import mlcompute

    # Select CPU device.
    mlcompute.set_mlc_device(device_name=‘cpu’) # Available options are 'cpu', 'gpu', and ‘any'.
