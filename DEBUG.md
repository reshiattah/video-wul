🔍 Troubleshooting & Technical Notes
1. eSpeak / pyttsx3 "Default Voice" Error
If you encounter ValueError: No default voice found or issues with gmw/en, it is usually because the system-level eSpeak drivers are not mapping correctly to Python.

Linux/Colab Fix:

Bash

sudo apt-get update && sudo apt-get install espeak -y
Monkey-Patching: If the error persists after installation, use the following patch before calling pyttsx3.init():

Python

from pyttsx3.drivers import espeak
espeak.EspeakDriver._defaultVoice = b'en' 
2. NumPy "Dtype Size Changed" Error
If you see errors regarding numpy.dtype size changes when importing Mimic3 or ONNX, it means there is a version mismatch between NumPy 1.x and 2.x.

Recommended Version: For maximum compatibility with Mycroft Mimic 3 and ONNX runtime, use:

Bash

pip uninstall numpy
pip install numpy==1.23.5
3. Memory Management (Large Models)
Running Stable Diffusion and TTS simultaneously can exceed 12GB of System RAM.

Tip: The generate_video function includes a finally block that clears temp_images/ and temp_audio/ after every run to prevent disk bloat.

CPU Mode: If running without a GPU, ensure torch_dtype=torch.float32 is used in the StableDiffusionPipeline, as float16 is often unsupported on standard CPUs.

4. Disabling Safety Checkers
To ensure the model does not block content during offline use, the pipeline is initialized with:

Python

pipe.safety_checker = None
