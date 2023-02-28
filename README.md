
# Automate your YouTube playlist downloads with this Python script

This code uses the Pytube library in Python to download YouTube videos from a playlist. The code allows you to specify the URL of the YouTube playlist, the directory where you want to save the downloaded videos, and the desired video resolution. The script loops through each video in the playlist and downloads the video to the specified directory with the specified resolution.

In addition to this, the code has been updated to include a feature that allows you to download specific videos from the playlist, rather than downloading all the videos in the playlist. This feature is optional and can be activated by specifying a list of video numbers to download.

This script can be useful for automating the process of downloading multiple YouTube videos from a playlist, saving time and effort. It could be particularly helpful for content creators who need to download videos for editing purposes or for individuals who want to save online tutorials or educational videos for later viewing.


## 🛠 Skills
Python ...


## Installation

Install Lib  with  

```bash
  pip install pytube
```
    
 ```bash
 import os
from pytube import Playlist, YouTube

# Set the URL of the YouTube playlist
playlist_url = "URL"

# Set the path to the directory where you want to save the downloaded videos
download_path = "Distination Path "

# Set the desired video resolution (720p in this case)
resolution = "720p"

# Set the list of video numbers to download (empty list means download all videos)
video_numbers_to_download = [1, 3, 5]

try:
    # Create a Pytube Playlist object from the playlist URL
    playlist = Playlist(playlist_url)

    # Filter videos based on video numbers to download (if specified)
    if video_numbers_to_download:
        filtered_videos = [video for i, video in enumerate(playlist.videos) if i+1 in video_numbers_to_download]
    else:
        filtered_videos = playlist.videos

    # Loop through each filtered video in the playlist
    for video in filtered_videos:
        # Set the resolution of the video
        video = YouTube(video.watch_url).streams.filter(res=resolution).first()

        # Set the path to save the video to
        video_path = os.path.join(download_path, video.title + ".mp4")

        # Download the video to the specified path
        video.download(output_path=download_path)

        print(f"Downloaded {video.title} to {video_path}")

except Exception as e:
    print("An error occurred during the download process:", e)
 ```




## 🔗 Links
[![portfolio](https://img.shields.io/badge/my_portfolio-000?style=for-the-badge&logo=ko-fi&logoColor=white)](https://github.com/AMF10)
[![linkedin](https://img.shields.io/badge/linkedin-0A66C2?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/abdelrahmanfaheem/)
 

