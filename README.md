# WebGuru - Website Summarizer and Q&A System

A sophisticated web application that combines web scraping, AI-powered content summarization, and intelligent question-answering capabilities. Built with Flask, this tool provides comprehensive website analysis through both a web interface and command-line interface.

## 🌟 Features

### Core Functionality
- **Web Scraping**: Iteratively scrape websites up to configurable depth levels
- **AI-Powered Summarization**: Generate intelligent summaries using Google Gemini AI
- **Question & Answer System**: Ask questions about scraped content using BERT-based QA models
- **Website Structure Visualization**: Create interactive network graphs showing website link structures
- **Content Embedding**: Advanced semantic search using sentence transformers

### Dual Interface
- **Web Application**: User-friendly Flask-based web interface
- **Command Line Tool**: Standalone Python script for batch processing

### Advanced Capabilities
- **Semantic Search**: Find relevant content using vector embeddings
- **Confidence Scoring**: Get reliability scores for AI-generated answers
- **Export Functionality**: Download summaries and visualizations
- **Session Management**: Persistent user sessions for web interface

## 🏗️ Architecture

### Technology Stack
- **Backend**: Flask (Python web framework)
- **AI Models**: 
  - Google Gemini 1.5 Pro for content summarization
  - BERT-based QA pipeline for question answering
  - Sentence Transformers for semantic embeddings
- **Data Processing**: BeautifulSoup4, NetworkX, Matplotlib
- **Web Scraping**: Requests library with error handling

### Project Structure
```
WebGuru/
├── app.py                 # Flask web application
├── final.py              # Command-line interface
├── templates/
│   └── index.html        # Web interface template
├── static/
│   ├── website_structure.png    # Generated visualizations
│   └── website_summary.txt      # Generated summaries
└── requirements.txt       # Python dependencies
```

## 🚀 Installation

### Prerequisites
- Python 3.7 or higher
- pip package manager
- Google Gemini API key

### Setup Instructions

1. **Clone the repository**
   ```bash
   git clone <repository-url>
   cd WebGuru
   ```

2. **Install dependencies**
   ```bash
   pip install -r requirements.txt
   ```

3. **Configure API keys**
   - Obtain a Google Gemini API key from [Google AI Studio](https://makersuite.google.com/app/apikey)
   - Update the API key in `app.py` and `final.py`:
     ```python
     genai.configure(api_key='YOUR_API_KEY_HERE')
     ```

4. **Run the application**
   ```bash
   # Web interface
   python app.py
   
   # Command line interface
   python final.py
   ```

## 📖 Usage

### Web Interface

1. **Start the Flask server**
   ```bash
   python app.py
   ```

2. **Open your browser** and navigate to `http://localhost:5000`

3. **Enter a URL** to analyze and click "Generate Summary"

4. **View results**:
   - AI-generated summary
   - Website structure visualization
   - Ask questions about the content

5. **Download results** using the download button

### Command Line Interface

1. **Run the script**
   ```bash
   python final.py
   ```

2. **Enter the target URL** when prompted

3. **Wait for processing**:
   - Website scraping
   - Content analysis
   - Summary generation

4. **Ask questions** interactively about the content

5. **Type 'exit'** to quit the program

## 🔧 Configuration

### Scraping Depth
Modify the `max_depth` parameter in the `scrape_website()` function:
```python
# Default depth is 1, increase for deeper analysis
scrape_website(start_url, max_depth=2)
```

### AI Models
The application supports multiple QA models. Uncomment your preferred model in `final.py`:
```python
# Current model
qa_pipeline = pipeline("question-answering", model="bert-large-uncased-whole-word-masking-finetuned-squad")

# Alternative models
# qa_pipeline = pipeline("question-answering", model="distilbert-base-uncased-distilled-squad")
# qa_pipeline = pipeline("question-answering", model="deepset/roberta-large-squad2")
```

### Output Paths
Customize file output locations:
```python
# Visualization output
visualize_links(start_url, links, "custom_path.png")

# Summary output
save_summary_to_file(summary, "custom_summary.txt")
```

## 📊 Output Files

### Generated Files
- **`website_structure.png`**: Network graph visualization of website links
- **`website_summary.txt`**: AI-generated content summary (downloadable)

### File Locations
- Web interface: Files are saved in the `static/` directory
- Command line: Files are saved in the current working directory

## 🛠️ API Endpoints

### Flask Routes
- **`GET /`**: Main page with forms
- **`POST /`**: Process URL submission or questions
- **`GET /download_summary`**: Download generated summary as text file

### Request Parameters
- **URL Form**: `url` - Target website URL
- **Question Form**: `question` - User question about content

## 🔒 Security Considerations

- **API Key Management**: Store API keys in environment variables for production
- **Rate Limiting**: Implement rate limiting for web scraping
- **Input Validation**: Validate URLs and user inputs
- **Session Security**: Flask secret key is randomly generated

## 🚨 Error Handling

The application includes comprehensive error handling for:
- Network request failures
- Invalid URLs
- API rate limits
- File I/O operations
- Model inference errors

## 📈 Performance Optimization

### Current Optimizations
- Efficient queue-based scraping algorithm
- Vectorized similarity calculations
- Configurable scraping depth
- Session-based caching

### Recommended Improvements
- Implement Redis caching for embeddings
- Add async processing for large websites
- Database storage for persistent content
- CDN integration for static files

## 🧪 Testing

### Manual Testing
1. Test with various website types (blogs, e-commerce, corporate)
2. Verify error handling with invalid URLs
3. Test question-answering with different content types
4. Validate file downloads and visualizations

### Automated Testing (Future Enhancement)
```bash
# Run tests (when implemented)
python -m pytest tests/
```

## 🤝 Contributing

### Development Setup
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Add tests if applicable
5. Submit a pull request

### Code Style
- Follow PEP 8 guidelines
- Add docstrings to all functions
- Include type hints where appropriate
- Maintain consistent error handling

## 📝 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 🙏 Acknowledgments

- **Google Gemini AI** for advanced content summarization
- **Hugging Face** for pre-trained QA models
- **Flask** for the web framework
- **BeautifulSoup4** for web scraping capabilities
- **NetworkX** for graph visualization

## 📞 Support

For issues, questions, or contributions:
- Create an issue on GitHub
- Contact the development team
- Check the documentation for common solutions

## 🔄 Version History

- **v1.0.0**: Initial release with web and CLI interfaces
- Core functionality: scraping, summarization, Q&A
- Basic visualization and export features

---

**Note**: This application requires an active internet connection and valid API keys to function properly. Ensure compliance with website terms of service and respect robots.txt files when scraping.
