# Web3 Messenger (Metaverse Chat)

A decentralized real-time messaging application built with Web3 technology, featuring blockchain-based authentication and a stunning 3D animated interface.

## Overview

Web3 Messenger is a modern chat application that leverages blockchain technology for user authentication and data storage. Users connect their crypto wallets to access the platform, creating a truly decentralized messaging experience. The application features a beautiful animated 3D background powered by Vanta.js and Three.js, providing an immersive metaverse-like interface.

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

## Key Components

- **Login**: Handles Web3 wallet authentication with animated background
- **Header**: Displays user avatar, username, and logout functionality
- **Messages**: Fetches and displays messages with live updates
- **SendMessage**: Input form for sending new messages
- **Message**: Individual message bubble with avatar and timestamp
- **Avatar**: Generates unique pixel-art avatars using DiceBear API

## Environment Variables

| Variable | Description |
|----------|-------------|
| `NEXT_PUBLIC_APP_ID` | Your Moralis application ID |
| `NEXT_PUBLIC_SERVER_URL` | Your Moralis server URL |

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

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## License

This project is open source and available under the MIT License.
