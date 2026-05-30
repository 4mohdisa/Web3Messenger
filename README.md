# Web3 Messenger (Metaverse Chat)

A decentralized real-time messaging application built with Web3 technology, featuring blockchain-based authentication and a stunning 3D animated interface.

## Overview

Web3 Messenger is a modern chat application that leverages blockchain technology for user authentication and data storage. Users connect their crypto wallets (via MetaMask or WalletConnect) to access the platform, creating a truly decentralized messaging experience. The application features a beautiful animated 3D background powered by Vanta.js NET effect and Three.js, providing an immersive metaverse-like interface.

Built with Next.js and React, this application demonstrates the integration of Web3 technologies with modern frontend frameworks. Messages are stored on Moralis's blockchain backend with real-time synchronization, ensuring data persistence and live updates across all connected clients.

## Features

- **🔐 Web3 Authentication**: Secure wallet-based login using Moralis and WalletConnect
- **💬 Real-time Messaging**: Live chat updates with automatic message synchronization
- **👤 Custom Usernames**: Users can set and update their display names
- **🎨 Dynamic Avatars**: Automatically generated pixel-art avatars based on usernames
- **⏰ Timestamp Display**: Messages show relative time using "time ago" format
- **🌐 3D Animated Background**: Interactive Vanta.js NET effect with Three.js
- **📱 Responsive Design**: Fully responsive UI built with Tailwind CSS
- **🔄 Live Data Sync**: Real-time message updates using Moralis live queries
- **💾 Decentralized Storage**: Messages stored on Moralis blockchain backend
- **⏱️ Message History**: Displays messages from the last 15 minutes
- **🎭 User Identification**: Messages color-coded by sender (user vs. others)
- **🖼️ DiceBear Integration**: Pixel-art avatars generated via DiceBear API

## Tech Stack

### Frontend
- **Next.js 12.3.1** - React framework for production
- **React 18.2.0** - UI library
- **Tailwind CSS 3.1.8** - Utility-first CSS framework

### Web3 & Blockchain
- **react-moralis 1.4.2** - Moralis SDK for React
- **@walletconnect/web3-provider 1.8.0** - WalletConnect integration

### 3D Graphics & Animation
- **Three.js 0.145.0** - 3D graphics library
- **Vanta.js 0.5.24** - Animated 3D backgrounds

### Additional Libraries
- **timeago-react 3.0.5** - Relative timestamp formatting

### Development Tools
- **ESLint 8.25.0** - Code linting and quality
- **PostCSS 8.4.18** - CSS processing
- **Autoprefixer 10.4.12** - CSS vendor prefixing

## Prerequisites

Before running this project, ensure you have:

- Node.js (v14 or higher)
- npm or yarn package manager
- A Moralis account with an app configured
- MetaMask or another Web3 wallet browser extension

## Installation

1. Clone the repository:
```bash
git clone <repository-url>
cd Web3Messenger
```

2. Install dependencies:
```bash
npm install
# or
yarn install
```

3. Configure environment variables:

Create a `.env.local` file in the root directory and add your Moralis credentials:

```env
NEXT_PUBLIC_APP_ID=your_moralis_app_id
NEXT_PUBLIC_SERVER_URL=your_moralis_server_url
```

You can find these values in your Moralis dashboard after creating a new app.

## Getting Started

Run the development server:

```bash
npm run dev
# or
yarn dev
```

Open [http://localhost:3000](http://localhost:3000) in your browser to see the application.

## Usage

1. **Connect Wallet**: Click "Login to the Metaverse" to connect your Web3 wallet
2. **Set Username**: After authentication, set your display name
3. **Send Messages**: Type your message in the input field and click send
4. **View Messages**: Messages from the last 15 minutes are displayed in real-time
5. **Change Username**: Click "Change Username" in the header to update your display name
6. **Logout**: Click on your avatar to disconnect your wallet

## Project Structure

```
Web3Messenger/
├── components/
│   ├── Avatar.js          # User avatar component with DiceBear API
│   ├── ChangeUsername.js  # Username update functionality
│   ├── Header.js          # App header with user info
│   ├── Login.js           # Web3 authentication screen
│   ├── Message.js         # Individual message component
│   ├── Messages.js        # Message list with live queries
│   └── SendMessage.js     # Message input and submission
├── pages/
│   ├── _app.js           # App wrapper with Moralis provider
│   ├── index.js          # Main chat interface
│   └── api/              # API routes
├── public/               # Static assets
├── styles/               # Global styles
└── package.json          # Dependencies and scripts
```

## Architecture

### Application Flow

1. **Authentication Layer**: Users authenticate via Moralis using their Web3 wallet (MetaMask/WalletConnect)
2. **Data Layer**: Messages are stored in Moralis database with real-time query subscriptions
3. **Presentation Layer**: React components render the UI with Tailwind CSS styling
4. **Visual Layer**: Vanta.js NET effect creates an animated 3D background

### Key Components

#### `Login.js`
- Handles Web3 wallet authentication using Moralis `authenticate()` method
- Features interactive Vanta.js NET effect background with mouse/touch controls
- Displays app logo and "Login to the Metaverse" button
- Configuration: Gray color scheme (0x616161), 10 points, 17.0 spacing

#### `Header.js`
- Sticky header with glassmorphism effect (black/30 backdrop blur)
- Displays app logo, user avatar, and username
- Grid layout (5 columns mobile, 6 columns desktop)
- Integrates `Avatar` and `ChangeUsername` components
- Avatar click triggers logout functionality

#### `Messages.js`
- Fetches messages using `useMoralisQuery` with live updates enabled
- Queries messages from last 15 minutes (configurable via `MINS_DURATION`)
- Scrollable container (30rem height) with glassmorphism background
- Auto-renders new messages in real-time
- Integrates `SendMessage` component at bottom

#### `SendMessage.js`
- Fixed bottom position with glassmorphism styling
- Saves messages to Moralis "Messages" collection
- Stores: message text, username, and Ethereum address
- Auto-scrolls to latest message on send
- Rounded pill-shaped input with send icon

#### `Message.js`
- Individual message bubble component
- Color-coded: gray for user messages, blue for others
- Displays avatar, message text, timestamp, and username
- Uses `TimeAgo` component for relative time display
- Responsive layout with flex positioning

#### `Avatar.js`
- Generates pixel-art avatars using DiceBear API
- URL format: `https://avatars.dicebear.com/api/pixel-art/{username}.svg`
- Rounded full with hover opacity effect
- Optional logout on click functionality

#### `ChangeUsername.js`
- Prompts user for new username via browser prompt
- Updates Moralis user data using `setUserData()` method
- Positioned absolutely in top-right corner
- Displays current username in prompt

#### `_app.js`
- Root application wrapper with `MoralisProvider`
- Dynamically loads Three.js from CDN on mount
- Configures Moralis with environment variables
- Handles script cleanup on unmount

#### `index.js`
- Main page component with conditional rendering
- Shows `Login` component when not authenticated
- Shows `Header` and `Messages` when authenticated
- Implements Vanta.js NET effect background
- Configuration: White color (0xffffff), black background, 10 points, 17.0 spacing

## Technical Implementation Details

### Moralis Integration

- **Authentication**: Uses `useMoralis` hook for wallet connection
- **Data Storage**: Messages stored in "Messages" collection with fields:
  - `message`: String - The message content
  - `username`: String - User's display name
  - `ethAddress`: String - User's Ethereum wallet address
  - `createdAt`: Date - Automatic timestamp
- **Live Queries**: Real-time updates via `useMoralisQuery` with `live: true` option
- **Query Filtering**: Messages filtered by creation time (last 15 minutes)
- **User Management**: Usernames stored in Moralis user object

### Vanta.js Configuration

The application uses two different Vanta.js NET configurations:

**Login Page:**
- Color: Gray (0x616161)
- Background: Black (0x0)
- Mouse/Touch controls: Enabled
- Points: 10.0
- Spacing: 17.0

**Main Chat Page:**
- Color: White (0xffffff)
- Background: Black (0x0)
- Mouse/Touch controls: Disabled
- Points: 10.0
- Spacing: 17.0

### Styling Approach

- **Glassmorphism**: Extensive use of backdrop-blur and semi-transparent backgrounds
- **Color Scheme**: Dark theme with black backgrounds and white/gray text
- **Responsive Grid**: CSS Grid for header layout (5/6 columns)
- **Flexbox**: Used for message alignment and component positioning
- **Tailwind Utilities**: Custom opacity values (e.g., `bg-black/40`, `bg-blue-400/30`)

### Message Time Filtering

Messages are filtered using Moralis query:
```javascript
query.greaterThan("createdAt", new Date(Date.now() - 1000 * 60 * MINS_DURATION))
```
Where `MINS_DURATION = 15 * 10000` (configurable)

## Environment Variables

| Variable | Description | Example |
|----------|-------------|----------|
| `NEXT_PUBLIC_APP_ID` | Your Moralis application ID | `IxH3EXzHhjDnQpiYYZRGnTw7YIFIYz90ubdn07X4` |
| `NEXT_PUBLIC_SERVER_URL` | Your Moralis server URL | `https://fncnvdqt3c7v.grandmoralis.com:2053/server` |

**Note**: See `example.local` file for reference configuration.

## Build & Deploy

Build the application for production:

```bash
npm run build
npm start
```

The application can be deployed on:
- **Vercel** (recommended for Next.js)
- **Netlify**
- Any Node.js hosting platform

### Deployment Checklist

1. Set up Moralis account and create new app
2. Configure environment variables in hosting platform
3. Ensure `.env.local` is in `.gitignore`
4. Build and test locally before deploying
5. Verify wallet connection works in production

## Known Limitations

- Messages are only displayed from the last 15 minutes
- No message persistence beyond Moralis database retention
- Requires active Moralis server connection
- DiceBear API dependency for avatar generation
- No message editing or deletion functionality
- No private/direct messaging support

## Browser Compatibility

- Chrome/Brave (recommended)
- Firefox
- Edge
- Safari (with MetaMask extension)

**Requirements:**
- Web3 wallet extension (MetaMask, WalletConnect compatible wallet)
- JavaScript enabled
- WebGL support for 3D effects

## Future Enhancements

- [ ] Message persistence beyond 15 minutes
- [ ] Private/direct messaging functionality
- [ ] Message reactions and emojis
- [ ] File/image sharing capabilities
- [ ] User presence indicators (online/offline)
- [ ] Message search functionality
- [ ] Custom avatar upload option
- [ ] Dark/light theme toggle
- [ ] Mobile app version
- [ ] IPFS integration for decentralized storage

## Troubleshooting

### Common Issues

**Wallet won't connect:**
- Ensure MetaMask or compatible wallet is installed
- Check that you're on a supported network
- Clear browser cache and try again

**Messages not appearing:**
- Verify Moralis server is running
- Check environment variables are correctly set
- Ensure messages are within 15-minute window

**3D background not loading:**
- Check browser WebGL support
- Verify Three.js script loaded correctly
- Try disabling browser extensions

**Username not updating:**
- Ensure you're authenticated
- Check Moralis user permissions
- Try logging out and back in

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

### Development Guidelines

1. Follow existing code style and conventions
2. Test thoroughly before submitting PR
3. Update documentation for new features
4. Ensure no breaking changes to existing functionality

## License

This project is open source and available under the MIT License.

## Acknowledgments

- **Moralis** - Web3 backend infrastructure
- **Vanta.js** - 3D animated backgrounds
- **DiceBear** - Avatar generation API
- **Next.js Team** - React framework
- **Tailwind CSS** - Utility-first CSS framework
