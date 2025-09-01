# Synology Video Player

A lightweight HTML5 video player designed for personal use on Synology NAS systems.

## Features

- Single HTML file deployment
- HTML5 video player with full controls
- Automatic video file scanning
- Responsive grid layout
- Keyboard shortcuts
- Support for MP4, WebM, AVI, MOV, MKV formats

## Setup Instructions

### Method 1: Web Station Deployment (Recommended)

1. **Enable Web Station** in Synology DSM Package Center
2. **Create a new virtual host** or use the default
3. **Upload files** to your web root directory (usually `/web/` or `/volume1/web/`)
4. **Create video folder** structure in the same directory
5. **Access** via `http://YOUR_NAS_IP:PORT/index.html`

### Method 2: File Station Access

1. **Place files** in any accessible folder (e.g., `/homes/username/`)
2. **Enable file sharing** for the folder in DSM Control Panel
3. **Access** via File Station's built-in web server

## Folder Structure

```
/web/
├── index.html          # Main video player file
├── videos.json         # Video manifest (optional)
└── videos/            # Video files directory
    ├── movie1.mp4
    ├── movie2.webm
    └── series/
        ├── episode1.mp4
        └── episode2.mp4
```

## Configuration Options

### Option 1: Manifest File (Recommended)

Create a `videos.json` file with your video list:

```json
{
  "videos": [
    {
      "title": "My Movie",
      "filename": "movie.mp4", 
      "path": "videos/movie.mp4",
      "format": "MP4"
    }
  ]
}
```

### Option 2: Folder Scanning

Enter the folder path in the interface and click "Scan Folder". This requires:

- Directory listing enabled in your web server
- Proper file permissions (755 for directories, 644 for files)

## File Permissions

Set proper permissions using SSH or DSM Terminal:

```bash
# For web directory
sudo chmod 755 /volume1/web/
sudo chmod 644 /volume1/web/index.html
sudo chmod 755 /volume1/web/videos/
sudo chmod 644 /volume1/web/videos/*
```

## Supported Video Formats

- MP4 (H.264/H.265)
- WebM (VP8/VP9)
- AVI
- MOV
- MKV
- OGG/OGV

## Keyboard Shortcuts

- **Space**: Play/Pause
- **F**: Toggle Fullscreen
- **M**: Mute/Unmute
- **←/→**: Seek backward/forward 10 seconds
- **↑/↓**: Volume up/down 10%
- **H**: Toggle keyboard shortcuts help

## Troubleshooting

### Videos Not Loading

1. **Check file permissions** - ensure files are readable
2. **Verify file paths** - make sure paths in manifest are correct
3. **Test direct access** - try accessing video URL directly
4. **Check browser console** for error messages

### Directory Scanning Issues

1. **Enable directory listing** in Web Station settings
2. **Check folder permissions** (755 required)
3. **Verify web server configuration**
4. **Use manifest file** as alternative

### Performance Issues

1. **Use lower resolution videos** for better streaming
2. **Enable hardware acceleration** in browser settings
3. **Check network connection** between device and NAS
4. **Consider video compression** for large files

## Browser Compatibility

- Chrome/Chromium 90+
- Firefox 88+
- Safari 14+
- Edge 90+

## Security Notes

- This player is designed for **personal/home use only**
- **Do not expose** to the internet without proper security measures
- **Use HTTPS** when accessing over network
- **Restrict access** to trusted devices only

## Customization

The player can be customized by editing the embedded CSS and JavaScript in the HTML file:

- **Colors**: Modify CSS custom properties
- **Layout**: Adjust grid breakpoints and spacing
- **Controls**: Add/remove keyboard shortcuts
- **Metadata**: Extend video object properties

## License

Free for personal use. Not intended for commercial distribution.