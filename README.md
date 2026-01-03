🐺 VideoWul AI
Standalone Offline Text-to-Video Generation

VideoWul AI is a powerful, entirely offline desktop application designed to transform natural language prompts into cinematic video content. By integrating local Large Language Models, Stable Diffusion, and advanced video synthesis, VideoWul AI ensures privacy, creative freedom, and high-performance rendering without requiring an internet connection.

🌟 Key Features
100% Offline Core: All generation—from speech synthesis to image rendering—happens locally on your hardware.

Uncensored Creative Freedom: Built-in Stable Diffusion pipeline with the safety checker disabled to allow for unrestricted artistic expression.

Programmatic Video Stitching: Uses MoviePy and FFmpeg for high-fidelity synchronization of visual frames and audio.

Modular Architecture: Independent modules for Text-to-Speech (TTS), Text-to-Image (T2I), and Video Compilation.

🛠️ Tech Stack
Language: Python 3.12+

UI Framework: PyQt5

Image Generation: Stable Diffusion v1.5 (via Hugging Face diffusers)

Audio Generation: Mycroft Mimic 3 / pyttsx3 (Offline-ready)

Video Processing: MoviePy with FFmpeg backend

Backend: PyTorch (CPU/CUDA)

📦 Installation & Setup
Prerequisites
Python 3.12

FFmpeg: Required for video encoding.

eSpeak: Required for the offline TTS engine.

Setup Instructions
Clone the Repository:

Bash

git clone https://github.com/yourusername/VideoWul-AI.git
cd VideoWul-AI
Install Core Dependencies:

Bash

pip install PyQt5 moviepy torch diffusers transformers accelerate gTTS pydub
Install Offline TTS (Mimic 3):

Bash

pip install ovos-tts-plugin-mimic3 ovos-plugin-manager mycroft-mimic3-tts
🚀 Generation Workflow
The VideoWul AI engine follows a structured 6-step pipeline to ensure synchronization and quality:

Segment Processing: Input text is parsed into logical sentences or segments.

TTS Synthesis: High-quality offline audio is generated for each segment (using Mimic 3).

T2I Rendering: Stable Diffusion generates high-detail frames for each segment.

Sync & Timing: Image duration is automatically matched to the length of the synthesized audio.

Compilation: Individual clips are concatenated using MoviePy.

Encoding: The final stream is exported via FFmpeg as a .mp4 file.

🖥️ Usage Example
Python

from videowul_core import generate_video

# Example prompt
text = "A futuristic city at sunset, flying cars reflecting neon lights."

# Generate video (Safety Checker Disabled)
generate_video(
    text_input=text,
    output_video_path="future_city.mp4",
    num_inference_steps=25
)
⚠️ Current Environment Status (Development Note)
While the core T2I and Video Compilation modules are fully functional, offline TTS integration can be environment-specific. In cloud-hosted environments like Google Colab, VideoWul AI may default to Silent Audio or gTTS (online) workarounds due to system-level driver restrictions for eSpeak. Full offline speaking capabilities are optimized for Standalone Desktop Installations.

📄 License
This project is licensed under the BSL-1.0 License (Boost Software License).
