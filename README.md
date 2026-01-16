# YouTube Downloader

A simple web-based YouTube video downloader application built with Flask and yt-dlp.

## Features

- 🎬 Download YouTube videos with a clean, modern web interface
- 📊 View video information before downloading (title, thumbnail, duration, uploader)
- ⚙️ Choose between best and worst quality downloads
- 💾 Videos are automatically saved to the `downloads` folder
- 🔄 Direct file download from the web interface
- 📱 Responsive design that works on desktop and mobile

## Requirements

- Python 3.6 or higher
- Flask
- yt-dlp

## Installation

1. **Clone or download this repository**

2. **Install required dependencies:**
   ```bash
   pip install flask yt-dlp
   ```

## Usage

1. **Start the application:**
   ```bash
   python app.py
   ```

2. **Open your browser:**
   - Navigate to `http://127.0.0.1:5000`
   - The Flask development server will run locally on port 5000

3. **Download a video:**
   - Paste a YouTube video URL into the input field
   - Select your preferred quality (Best or Worst)
   - Click the "Get Info" button to preview video details
   - Click the "Download" button to download the video
   - The video will be saved to the `downloads` folder

## Project Structure

```
YOUTUBE DOWNLOADER/
├── app.py                  # Flask backend application
├── README.md              # This file
├── how_to_run.txt         # Quick start guide
├── downloads/             # Downloaded videos folder (created automatically)
└── templates/
    └── index.html         # Web interface
```

## API Endpoints

### GET `/`
Returns the main web interface.

### POST `/download`
Downloads a YouTube video.
- **Request Body:**
  ```json
  {
    "url": "https://www.youtube.com/watch?v=...",
    "quality": "best"  // or "worst"
  }
  ```
- **Response:** JSON with filename, title, and success status

### POST `/get-info`
Retrieves video information without downloading.
- **Request Body:**
  ```json
  {
    "url": "https://www.youtube.com/watch?v=..."
  }
  ```
- **Response:** JSON with title, thumbnail, duration, and uploader

### GET `/download-file/<filename>`
Downloads a video file from the downloads folder.

## Notes

- Downloaded videos are saved in the `downloads` folder with their original YouTube titles
- The first time you run the application, the `downloads` folder will be created automatically
- Make sure the video URL is a valid YouTube URL
- Large videos may take time to download depending on your internet connection

## Troubleshooting

**Issue:** "yt-dlp is not installed"
- Solution: Run `pip install yt-dlp`

**Issue:** Port 5000 is already in use
- Solution: Change the port in `app.py` by modifying `app.run(debug=True)` to `app.run(debug=True, port=5001)`

**Issue:** Unable to download videos
- Solution: Make sure you have a stable internet connection and yt-dlp is up to date. Run `pip install --upgrade yt-dlp`

## License

This project is open source and available for personal use.

## Support

For issues with yt-dlp, visit: https://github.com/yt-dlp/yt-dlp
