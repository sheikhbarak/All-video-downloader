import yt_dlp

def download_video(url, output_path="downloads"):
    ydl_opts = {
        'outtmpl': f'{output_path}/%(title)s.%(ext)s',
        'format': 'bestvideo+bestaudio/best',  # Best quality
        'quiet': False,  # Show progress
    }

    try:
        with yt_dlp.YoutubeDL(ydl_opts) as ydl:
            info = ydl.extract_info(url, download=True)
            print(f"Downloaded: {info.get('title', 'Untitled')}")
    except Exception as e:
        print(f"Error: {str(e)}")

# Example usage (works for YouTube, TikTok, Instagram, etc.):
download_video("https://www.tiktok.com/@user/video/123456789")
