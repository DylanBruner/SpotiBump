# SpotiBump 🎵

A web application that displays your currently playing Spotify track and provides quick actions to like, dislike, or "bump" songs. The bump feature removes and re-adds a track to your liked songs, which can be useful for refreshing your music recommendations.

## ✨ Features

- **Real-time Track Display**: Shows your currently playing Spotify track with album art
- **Quick Actions**: Like, dislike, or bump songs with a single click
- **Auto-refresh**: Updates the current track every 5 seconds
- **Long Sessions**: Uses refresh tokens to keep you logged in for extended periods
- **Auto-bump**: Support for `?bump=true` query parameter to automatically bump songs
- **Modern UI**: Clean, responsive design with Spotify-inspired styling

## 🚀 Quick Start

### Prerequisites

- A Spotify account
- A Spotify Developer application (free)

### Setup

1. **Create a Spotify App**:
   - Go to [Spotify Developer Dashboard](https://developer.spotify.com/dashboard)
   - Click "Create App"
   - Fill in the app details:
     - **App name**: SpotiBump (or any name you prefer)
     - **App description**: A web app for managing Spotify tracks
     - **Website**: `http://127.0.0.1:3000`
     - **Redirect URI**: `http://127.0.0.1:3000`
   - Accept the terms and create the app

2. **Get Your Client ID**:
   - In your Spotify app dashboard, copy the **Client ID**
   - Replace the `CLIENT_ID` constant in `index.html` (line 82) with your actual Client ID

3. **Run the Application**:
   ```bash
   # Using Python (if you have it installed)
   python -m http.server 3000
   
   # Or using Node.js (if you have it installed)
   npx http-server -p 3000
   
   # Or using PHP (if you have it installed)
   php -S 127.0.0.1:3000
   ```

4. **Open in Browser**:
   - Navigate to `http://127.0.0.1:3000`
   - Click "Login with Spotify"
   - Authorize the application

## 🎯 Usage

### Basic Features

- **View Current Track**: The app automatically displays your currently playing track
- **Like/Unlike**: Click the ❤️ button to add/remove tracks from your liked songs
- **Dislike**: Click the 👎 button to remove tracks from your liked songs
- **Bump**: Click the 🔄 button to remove and re-add a track (useful for refreshing recommendations)

### Auto-bump Feature

You can automatically bump the currently playing song by adding `?bump=true` to the URL:

```
http://127.0.0.1:3000/?bump=true
```

This is useful for:
- **Bookmarks**: Save the URL for quick one-click bumping
- **Automation**: Use in scripts or automation tools
- **Quick Access**: Bump without opening the full interface

The auto-bump feature works whether you're logged in or not - if you're not logged in, it will prompt you to authenticate first, then automatically bump the song.

## 🔧 Technical Details

### Authentication Flow

The app uses Spotify's OAuth 2.0 PKCE (Proof Key for Code Exchange) flow for secure authentication:

1. **Authorization Request**: User clicks login → redirected to Spotify
2. **User Authorization**: User grants permissions on Spotify
3. **Code Exchange**: App exchanges authorization code for access token
4. **Token Refresh**: App automatically refreshes tokens when they expire

### API Endpoints Used

- `GET /me/player/currently-playing` - Get current track
- `GET /me/tracks/contains` - Check if track is saved
- `PUT /me/tracks` - Add track to liked songs
- `DELETE /me/tracks` - Remove track from liked songs

### Permissions Required

- `user-read-currently-playing` - Read currently playing track
- `user-library-modify` - Add/remove tracks from liked songs
- `user-library-read` - Check if tracks are saved

## 🛠️ Development

### Project Structure

```
SpotiBump/
├── index.html          # Main application file
└── README.md          # This file
```

### Key Components

- **Authentication**: OAuth 2.0 PKCE flow with refresh token support
- **Track Display**: Real-time updates of currently playing track
- **API Integration**: Direct Spotify Web API calls
- **UI**: Responsive design with modern styling

### Customization

You can easily customize the app by modifying:

- **Styling**: Update the CSS in the `<style>` section
- **Functionality**: Modify the JavaScript functions
- **Endpoints**: Add new Spotify API endpoints
- **Features**: Extend with additional track management features

## 🔒 Security

- **PKCE Flow**: Uses secure OAuth 2.0 PKCE authentication
- **No Server**: All authentication happens client-side
- **Token Storage**: Tokens stored in browser localStorage
- **Automatic Cleanup**: Tokens are cleared when invalid

## 🐛 Troubleshooting

### Common Issues

**"Invalid Client ID"**
- Make sure you've replaced the `CLIENT_ID` in the code with your actual Spotify app Client ID

**"Redirect URI Mismatch"**
- Ensure your Spotify app's redirect URI is exactly `http://127.0.0.1:3000`

**"No track currently playing"**
- Make sure you have Spotify open and playing music
- The app only shows tracks playing in the Spotify desktop/web app

**"Token expired"**
- The app should automatically refresh tokens, but if it fails, try logging out and back in

### Debug Mode

Open your browser's developer console (F12) to see detailed logs about:
- Authentication flow
- API requests
- Token refresh attempts
- Auto-bump execution

## 📝 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Feel free to submit issues, feature requests, or pull requests to improve SpotiBump!

## 🙏 Acknowledgments

- [Spotify Web API](https://developer.spotify.com/documentation/web-api/) for the music data
- Spotify's OAuth 2.0 implementation for secure authentication
- The open source community for inspiration and tools

---

**Note**: This is a personal project and is not affiliated with Spotify. Use at your own discretion. 