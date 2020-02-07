# Installing GSAM

Installing GSAM consists of two steps: download the package and add it to the MATLAB PATH.

## 1. Download GSAM

### Option A: Using git (recommended)

Cloning the GitHub repository makes it easier to keep updated with the latest version.

Open the terminal or command prompt and navigate to the directory where you would like to download GSAM.
```bash
cd mydirectory  # replace "mydirectory" with the path where you want to install

git clone https://github.com/JonathanRob/GeneSetAnalysisMatlab.git
```

### Option B: Download directly from GitHub

Navigate to the [GSAM repository](https://github.com/JonathanRob/GeneSetAnalysisMatlab) and press the "Clone or download" button, then choose "Download ZIP". Download and unzip the file into the directory of your choice.


## 2. Add GSAM to the MATLAB PATH

Open MATLAB and add the GSAM directory to the path
```matlab
addpath('mydirectory/GeneSetAnalysisMatlab');  % replace "mydirectory" with actual location

savepath;  % to avoid having to add the path every time you start MATLAB
```

That's it!

Check out the [User guide](userguide.md) for more instructions on using GSAM.

