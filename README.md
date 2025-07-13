# Vibe-Chess

# VibeChess

A real-time multiplayer chess platform featuring collaborative gameplay modes designed for streamers and content creators. Built with React/TypeScript frontend and ASP.NET Core backend with SignalR for real-time communication.

## 🎮 Game Modes

### **Pawn Stars Mode** (Primary Feature)

Collaborative chess where multiple players control individual pieces in team-based gameplay:

#### **Captain Mode**

- **Two Captains** lead White and Black teams
- **Players join lobbies** using invite codes and are assigned to teams
- **Captains select which piece moves** each turn
- **Team members control their assigned pieces** and decide where to move
- Perfect for **streamer vs streamer** content with audience participation

#### **No-Captain Mode**

- **Players control individual pieces** without team leaders
- **Automated piece selection** for turns
- **Timer-based gameplay** (10 seconds per move)
- Great for **community chess events**

### **Classic Chess**

- Traditional 1v1 chess gameplay
- Stockfish engine integration for analysis
- Move history and evaluation

## 🏗️ Architecture

### **Backend** (ASP.NET Core 8)

- **SignalR Hub** for real-time communication
- **Redis** for game state and session management
- **Orchestrator Pattern** for clean separation of concerns
- **RESTful API** for lobby and game management

### **Frontend** (React + TypeScript + Vite)

- **Real-time UI updates** via SignalR
- **Interactive chessboard** with drag-and-drop
- **Lobby management** with team assignment
- **Responsive design** for desktop and mobile

### **Key Technologies**

- **SignalR**: WebSocket communication
- **Redis**: In-memory game state storage
- **Stockfish**: Chess engine for analysis
- **react-chessboard**: Interactive chess UI
- **chess.js**: Chess game logic

## 🚀 Getting Started

### Prerequisites

- [.NET 8 SDK](https://dotnet.microsoft.com/download/dotnet/8.0)
- [Node.js](https://nodejs.org/) (v18+ recommended)
- [Redis](https://redis.io/) (local or cloud instance)

### Backend Setup

1. **Navigate to Backend folder**

   ```bash
   cd Backend
   ```

2. **Install dependencies**

   ```bash
   dotnet restore
   ```

3. **Configure Redis** (update `appsettings.json`)

   ```json
   {
     "Redis": {
       "ConnectionString": "localhost:6379"
     }
   }
   ```

4. **Run the backend**
   ```bash
   dotnet run
   ```
   Backend will be available at `https://localhost:7139`

### Frontend Setup

1. **Navigate to Frontend folder**

   ```bash
   cd Frontend
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Run the development server**
   ```bash
   npm run dev
   ```
   Frontend will be available at `http://localhost:5173`

## 🎯 How to Play

### Creating a Lobby

1. **Choose game mode** (Captain or No-Captain)
2. **Set player limit** and timer settings
3. **Share invite codes** with players:
   - **Main invite code**: Becomes team captain
   - **Team-specific codes**: Join as regular player

### Joining a Game

1. **Use main invite code** to become a captain (if no captain exists for that team)
2. **Use team invite codes** to join as a regular player
3. **Wait for both teams** to have captains (Captain mode)
4. **Start the game** when ready

### Gameplay Flow

1. **Captain selects** which piece to move (Captain mode)
2. **Piece owner** chooses the destination square
3. **Move is validated** and broadcast to all players
4. **Game continues** until checkmate, stalemate, or draw

## 🔧 Development

### Project Structure

```
VibeChess/
├── Backend/
│   ├── Controllers/          # REST API endpoints
│   ├── Hubs/                # SignalR hubs (thin layer)
│   ├── Services/            # Business logic
│   │   ├── Hub/            # Hub orchestrators
│   │   ├── Game/           # Game management
│   │   ├── Lobby/          # Lobby management
│   │   └── Shared/         # Shared services
│   ├── Models/             # Data models
│   ├── DTOs/               # Data transfer objects
│   └── Configuration/      # App configuration
├── Frontend/
│   ├── src/
│   │   ├── components/     # React components
│   │   ├── contexts/       # React contexts
│   │   ├── hooks/          # Custom hooks
│   │   └── services/       # API services
│   └── public/             # Static assets
└── docs/                   # Technical documentation
```

### Key Design Patterns

- **Thin Hub Pattern**: SignalR hubs delegate to orchestrator services
- **Orchestrator Pattern**: Separates concerns for lobby and game operations
- **Service Layer**: Clean separation of business logic
- **Event Broadcasting**: Centralized real-time event management

## 🔄 Real-time Features

- **Live game state updates** for all connected players
- **Player join/leave notifications** in lobbies
- **Move broadcasting** with validation
- **Reconnection handling** for dropped connections
- **Game timer synchronization** across all clients

## 🎵 Additional Features

- **Spotify Integration**: Floating music player widget
- **Engine Analysis**: Stockfish-powered move evaluation
- **Sound Effects**: Move, capture, and check sounds
- **Responsive Design**: Works on desktop and mobile
- **Move History**: Navigate through game moves

## 🔮 Future Enhancements

- **User Authentication**: Player accounts and statistics
- **Game History**: Persistent storage of completed games
- **Spectator Mode**: Watch games without participating
- **Tournament Mode**: Bracket-based competitions
- **Advanced Analytics**: Move analysis and player insights
- **Mobile App**: Native iOS and Android applications

## 📄 License

This project is for educational and portfolio demonstration purposes.

---

**Built with ❤️ for the chess and streaming communities**
