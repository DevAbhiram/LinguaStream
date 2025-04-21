# LinguaStream

LinguaStream is a web application that allows users to download YouTube videos, translate them into different languages, and create dubbed versions with synthesized speech.

## Features

* Download YouTube videos
* Extract audio from videos
* Transcribe audio to text using Google Cloud Speech-to-Text
* Translate text to a target language using Google Cloud Translate
* Generate speech from translated text
* Merge translated audio with the original video
* Stream or download the final dubbed video

## Prerequisites

* Node.js (v14 or higher)
* npm (v6 or higher)
* Google Cloud account with enabled APIs:
  * Speech-to-Text API
  * Translate API

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/linguastream.git
   cd linguastream
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up Google Cloud credentials:
   * Create a service account in the Google Cloud Console
   * Download the JSON key file
   * Set the environment variable:
     ```bash
     export GOOGLE_APPLICATION_CREDENTIALS="path/to/your/service-account-file.json"
     ```

## Project Structure

```
linguastream/
├── node_modules/        # Node.js dependencies
├── public/              # Frontend static files
├── processing/          # Temporary storage for processed videos
├── app.js              # Main application file
├── routes.js           # API route handlers
├── services.js         # Video processing logic
├── package.json        # Project configuration
└── package-lock.json   # Dependency lock file
```

## API Endpoints

* `POST /api/process-video`: Start video processing with YouTube URL and target language
* `GET /api/job-status/:jobId`: Check the status of a processing job
* `GET /api/stream/:jobId`: Stream the processed video
* `GET /api/download/:jobId`: Download the processed video

## Usage

1. Start the server:
   ```bash
   node app.js
   ```

2. Access the application in your browser at `http://localhost:5000`

3. Enter a YouTube URL and select a target language for dubbing

4. Wait for the processing to complete, then stream or download the video

## Technical Process

1. **Video Download**: Uses ytdl-core to download YouTube videos
2. **Audio Extraction**: Uses fluent-ffmpeg to extract audio from the video
3. **Transcription**: Uses Google Cloud Speech-to-Text to convert audio to text
4. **Translation**: Uses Google Cloud Translate to translate text to target language
5. **Speech Generation**: Uses Google TTS API to generate spoken audio from translated text
6. **Audio/Video Merging**: Uses fluent-ffmpeg to combine original video with translated audio

## Limitations

* Processing large videos may take significant time
* Google Cloud Speech-to-Text has accuracy limitations
* Google TTS API has character limits per request (handled by splitting text)
* Free tier API usage limits apply to Google Cloud services

## Future Improvements

* Add user authentication
* Support multiple video formats
* Implement batch processing
* Add subtitle generation option
* Improve speech timing and sync with video

## License

[MIT License](LICENSE)

## Acknowledgements

* [ytdl-core](https://github.com/fent/node-ytdl-core)
* [fluent-ffmpeg](https://github.com/fluent-ffmpeg/node-fluent-ffmpeg)
* [Google Cloud Speech-to-Text](https://cloud.google.com/speech-to-text)
* [Google Cloud Translate](https://cloud.google.com/translate)
