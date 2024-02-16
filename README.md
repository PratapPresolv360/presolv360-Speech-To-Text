# Presolv60-Speech-To-Text

We used Whishper is an open-source project that provides audio transcription.
Presolv360-Speech-To-Text The audio refining functionality aims to improve the quality and accuracy of transcribed audio content within the Whishper application. This feature set includes a range of tools and techniques designed to enhance the clarity, remove noise, correct errors, and optimize the transcription process.

## Requirements

You will need the following tools installed on your machine to develop Whishper:

- Golang 1.20+
- NodeJS
- Docker

## Initial Setup

1. Clone the repository:

```bash
git clone https://github.com/PratapPresolv360/presolv360-Speech-To-Text.git
```

2. Bring up the containers needed for development:

```bash
docker-compose up -f docker-compose.yml -f docker-compose.dev.yml -d mongo transcription-api translate
```

**Tip:** You can install MongoDB Compass to connect to the database and see the data with a GUI.

## Running the Backend

1. Run the backend:

```bash
# Change to the backend directory
cd backend
# Run the backend
go run . -dev -updir ../whishper_data/uploads -asr localhost:8000 -translation localhost:5000 -db localhost:27017
```

## Running the Frontend

1. Add the following `.env` file inside the frontend folder:

```
PUBLIC_API_HOST=http://localhost:8080
PUBLIC_TRANSLATION_API_HOST=http://127.0.0.1:5000
PUBLIC_INTERNAL_API_HOST=http://127.0.0.1:8080
```

2. Then, run the frontend:

```bash
# Change to the frontend directory:
cd frontend
# Install dependencies:
npm install
# Run the development server:
npm run dev
```

### Audio Quality Enhancement in Whishper

As part of this fork, I am implementing audio quality enhancement features within the Whishper application. This enhancement aims to improve the clarity, accuracy, and overall quality of transcribed audio content. Key components of the audio refining functionality include:

- **Noise Reduction**: Implementing algorithms to reduce background noise and interference in audio recordings, enhancing clarity.
- **Speech Enhancement**: Developing tools to improve speech intelligibility and reduce distortion, ensuring clearer transcriptions.
- **Automatic Error Correction**: Integrating algorithms for detecting and rectifying transcription errors automatically, improving accuracy.
- **Speaker Diarization**: Implementing speaker segmentation algorithms to identify different speakers in the audio, enhancing context understanding.
- **Transcription Quality Metrics**: Developing metrics and evaluation tools to assess transcription accuracy and quality objectively.
- **User-Friendly Interface**: Designing an intuitive interface for users to access and customize the audio quality enhancement features seamlessly.

By integrating these enhancements, the Whishper application will provide users with improved audio transcription capabilities, resulting in clearer, more accurate transcriptions for various use cases.

## Project structure

Whishper is a collection of pieces that work together. The three main pieces are:

- Transcription-API: This is the API that enables running Faster-Whisper. You can find it in the `transcription-api` folder.
- Whishper-Backend: This is the backend that coordinates frontend calls, database, and tasks. You can find it in `backend` folder.
- Whishper-Frontend: This is the frontend (web UI) of the application. You can find it in `frontend` folder.
- Translation (3rd party): This is the libretranslate container that is used for translating subtitles.
- MongoDB (3rd party): This is the database that stores all the information about your transcriptions.
- Nginx (3rd party): This is the proxy that allows running everything from a single domain.
