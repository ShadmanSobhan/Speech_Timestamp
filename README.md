# Speech_Timestamp
This project allows you to search for a spoken phrase in a video and retrieve its timestamp, using OpenAI’s Whisper automatic speech recognition (ASR) model.

The used video is publicly available in -

https://drive.google.com/file/d/1LnXappv2zIwaknKvvNMjKp8oJKNgAwAC/view?usp=drive_link

#Dependencies

● whisper: ASR model for transcribing audio from video.

● ffmpeg-python: Audio extraction backend for Whisper.

● gdown: For downloading videos from Google Drive.

#Methodology

● Uses gdown to bypass Google Drive's web interface and download files via file ID.

● Encodes the binary content of the video using Base64. Why Base64?: HTML doesn’t allow embedding binary data directly. Base64 encodes binary streams into ASCII so that the video can be inlined via a data: URI.

● Why FFmpeg?

- Whisper relies on FFmpeg to:

   - Extract audio from video files

   - Resample to 16 kHz mono PCM format (pcm_s16le)

   - Pipe audio as raw input for Whisper’s transcription model

● Performs a case-insensitive substring match of the query.

● Returns the start time of the segment where the phrase occurs.

● Limitation: Only exact substring matches are detected. No fuzzy search or partial matching yet.

