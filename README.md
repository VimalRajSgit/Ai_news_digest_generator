# AI News Digest Generator

An automated news digest generator that creates professional video content using AI models for content curation, script writing, image generation, and video production.

## 🎬 Features

- **📰 Content Curation**: Automated RSS feed scraping and intelligent story selection
- **✍️ AI Script Writing**: Natural language script generation with proper news structure
- **🎨 Image Generation**: AI-generated visuals using SSD-1B for each news segment
- **🎙️ Text-to-Speech**: Natural voice synthesis with female voice options
- **🎬 Video Assembly**: Automated video production with smooth transitions and effects
- **🔄 Memory Efficient**: Smart model loading/unloading to manage GPU memory

## 🤖 AI Models Used

- **Qwen2-1.5B-Instruct**: Content analysis and script writing
- **segmind/SSD-1B**: High-quality image generation
- **SpeechT5**: Natural text-to-speech synthesis
- **LangGraph**: Workflow orchestration

## 🚀 Quick Start

### Prerequisites

- Python 3.8+
- CUDA-compatible GPU (recommended)
- 8GB+ GPU memory
- Internet connection for model downloads

### Installation

1. **Clone the repository:**
   ```bash
   git clone <repository-url>
   cd AI-News-Digest-Generator
   ```

2. **Install dependencies:**
   ```bash
   pip install -r requirements.txt
   ```
   
   Or install manually:
   ```bash
   pip install bitsandbytes accelerate feedparser langgraph moviepy diffusers transformers datasets soundfile huggingface_hub
   ```

3. **Run the notebook:**
   ```bash
   jupyter notebook AI_News_Digest_Generator.ipynb
   ```

### Environment Setup

The notebook automatically detects your environment:
- **Kaggle**: Uses `/kaggle/working/` directory
- **Google Colab**: Uses `/content/` directory
- **Local**: Uses current working directory

## 📋 Usage

### Basic Usage

1. **Open the Jupyter notebook**
2. **Run all cells sequentially** (Cell → Run All)
3. **Wait for completion** (typically 10-15 minutes)
4. **Download the generated video** from the output directory

### Advanced Configuration

#### RSS Feeds
Modify the `RSS_FEEDS` dictionary to add your preferred news sources:

```python
RSS_FEEDS = {
    "world_news": ["http://feeds.bbci.co.uk/news/world/rss.xml"],
    "tech_news": ["https://techcrunch.com/feed/"],
    "business": ["https://www.cnbc.com/id/100003114/device/rss/rss.html"]
}
```

#### Model Parameters
Adjust generation parameters in the notebook:

- **Image Generation**: Modify `num_inference_steps`, `guidance_scale`
- **Text-to-Speech**: Change speaker voice or generation parameters
- **Script Length**: Adjust `MAX_WORDS_PER_SEGMENT`

## 🏗️ Architecture

### Workflow Pipeline

```
RSS Feeds → Content Curation → Analysis → Script Writing → Visual Planning → Image Generation → Audio Generation → Video Assembly
```

### Agent Classes

1. **NewsCuratorAgent**: Fetches and ranks news stories
2. **AnalystAgent**: Provides context analysis
3. **ScriptWriterAgent**: Generates structured news scripts
4. **VisualDirectorAgent**: Creates image prompts using AI
5. **ProductionAgent**: Handles image/audio generation and video assembly

### Memory Management

The pipeline uses a memory-efficient approach:
- Models are loaded/unloaded as needed
- GPU memory is cleared between phases
- Quantized models reduce memory usage

## 📁 Output Structure

```
outputs/
├── news_digest_ssd1b_[seed].mp4    # Final video
├── segment_0_intro_[seed].png      # Intro image
├── segment_1_news_[seed].png       # News images
├── audio_segment_0_intro_[seed].wav # Audio files
└── ...
```

## ⚙️ Configuration Options

### Image Generation
- **Model**: segmind/SSD-1B
- **Resolution**: 1280x720
- **Steps**: 30
- **Guidance Scale**: 8.0

### Text-to-Speech
- **Model**: SpeechT5
- **Voice**: Female (configurable)
- **Sample Rate**: 16kHz

### Video Settings
- **FPS**: 24
- **Codec**: H.264
- **Audio Codec**: AAC
- **Duration**: Variable (based on content)

## 🔧 Troubleshooting

### Common Issues

1. **CUDA Out of Memory**
   - Reduce batch sizes
   - Use CPU fallback for some models
   - Clear GPU cache between operations

2. **Model Download Failures**
   - Check internet connection
   - Verify Hugging Face access
   - Try different mirror servers

3. **Audio Generation Issues**
   - Ensure soundfile is properly installed
   - Check audio codec support
   - Verify TTS model loading

4. **Video Assembly Problems**
   - Install ffmpeg
   - Check MoviePy dependencies
   - Verify file permissions

### Performance Optimization

- **GPU Memory**: Use 4-bit quantization for LLM
- **Processing Speed**: Enable xformers if available
- **Storage**: Clear cache directories regularly

## 📊 System Requirements

### Minimum Requirements
- Python 3.8+
- 8GB RAM
- 4GB GPU memory
- 10GB free disk space

### Recommended Requirements
- Python 3.9+
- 16GB RAM
- 12GB GPU memory (RTX 3080+)
- 20GB free disk space
- CUDA 11.8+

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **Hugging Face** for model hosting and transformers library
- **LangGraph** for workflow orchestration
- **MoviePy** for video processing
- **OpenAI** for inspiration and methodology

## 📞 Support

For issues and questions:
- Create an issue on GitHub
- Check the troubleshooting section
- Review the notebook documentation

## 🔄 Updates

### Version 1.0.0
- Initial release
- SSD-1B image generation
- Qwen2-1.5B script writing
- SpeechT5 audio synthesis
- Automated video assembly

---

**Note**: This project is for educational and research purposes. Please respect content usage rights and terms of service for all external APIs and services used.
