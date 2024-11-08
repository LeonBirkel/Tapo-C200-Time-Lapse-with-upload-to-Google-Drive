# RTSP Timelapse and Google Drive Upload (Dockerized)

This project captures timelapse images from an RTSP camera stream and automatically uploads them to Google Drive. It's designed to run efficiently in a Docker container, making it easy to deploy on various platforms, including a Raspberry Pi.

## Features

- Captures images from an RTSP camera stream at specified intervals.
- Uploads captured images to a Google Drive folder.
- Deletes local image copies after successful uploads (optional).
- Dockerized for easy deployment and portability.
- Configurable settings for camera URL, Google Drive credentials, and time interval.

## Requirements
- **RTSP Camera:** An IP camera that provides an RTSP stream. (Tapo C200 for example)
### If you want cloud storage
- **Google Drive Account:** A Google account with a folder to store the timelapse images.
- **Service Account:** A Google Cloud service account with permissions to upload files to your Google Drive folder.
### If you want a Container
- **Docker:**  Installed on your host machine (e.g., Raspberry Pi, server, or local computer).

## Setup

1. **Clone the Repository:**

   ```bash
   git clone https://github.com/LeonBirkel/RTSP_timelapse_and_gdrive_uplaod_dockerized
   cd RTSP_timelapse_and_gdrive_uplaod_dockerized

2. (Cloud Storage) Create a Google Service Account:

   In your Google Cloud console, create a service account.
   Grant the service account "Editor" or "Writer" access to the Google Drive folder where you want to store the images.
   Download the service account key file (key.json) and place it in the project directory.

3. Configure Settings:

   Create a config.py file in the project directory, rename and change config-example.py.  

4. Configuration
   config.py:
      RTSP_URL: Set the RTSP URL of your camera.
      SCREENSHOT_INTERVAL: How often a screenshot is taken.
      FOLDER_ID: Google Drive Folder as upload targer.
   capture.py:
      dir: Change the directory where images are temporarily stored (default is "timelapse").

## Usage
Once the program is running, it will automatically capture images from your RTSP camera at the specified interval and upload them to your Google Drive folder.

## Notes
Raspberry Pi: To run this on a Raspberry Pi, use the arm64v8/python:3.13-slim base image in the Dockerfile.
Error Handling: The script includes basic error handling, but you might want to add more robust error handling for production use.
Resource Usage: Monitor the resource usage of the container, especially on resource-constrained devices like the Raspberry Pi.
Security: Be mindful of security best practices when using service accounts and storing credentials.

## Future work
- converting the single images to a video


