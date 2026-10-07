# Eval Guesser

A chess training application that combines position evaluation practice with playing against Stockfish. Master chess evaluation by testing your positional understanding against the world's strongest chess engine.

## Features

### 🎮 Play vs Computer
Challenge Stockfish at various skill levels from beginner to master.

- **Adjustable Difficulty**: 20 skill levels to match any player strength
- **Color Selection**: Play as white or black
- **Real-time Evaluation**: Optional evaluation bar showing position assessment
- **Move History**: Track all moves in standard algebraic notation
- **Game Controls**: New game and undo functionality
- **Clean Interface**: Distraction-free playing experience

### 📊 Analysis Board
Analyze any chess position with deep Stockfish evaluation.

- **FEN Support**: Load any position via FEN string
- **Deep Analysis**: Configurable analysis depth (1-20)
- **Multi-line Analysis**: See top 5 best moves with evaluations
- **Real-time Updates**: Live position evaluation as you explore moves
- **Move List**: Comprehensive list of best moves with centipawn evaluations
- **Evaluation Bar**: Visual representation of position assessment

### 🎯 Eval Guesser Game (Coming Soon)
Test your evaluation skills by guessing Stockfish's position assessment.

- Compare your evaluation to Stockfish's analysis
- Track accuracy over time
- Learn to recognize critical position features

## Technical Details

### Evaluation System
- Evaluations are measured in **centipawns** (1/100th of a pawn)
- All evaluations are from white's perspective for consistency
- Positive values favor white, negative values favor black
- Checkmate evaluations show as "Mate in X"

### Architecture

#### Frontend
- **Framework**: SvelteKit with TypeScript
- **Chess Board**: Chessground (lichess board library)
- **Chess Logic**: chess.js for move validation
- **Styling**: Tailwind CSS for responsive design

#### Chess Engine
- **Engine**: Stockfish 16 NNUE compiled to WebAssembly
- **Communication**: UCI protocol via Web Workers
- **Analysis**: Multi-principal variation (MultiPV) support
- **Performance**: Runs entirely in the browser

### Key Components

#### `EvaluationBar.svelte`
Visual evaluation display that updates in real-time based on Stockfish analysis. Properly handles checkmate positions and shows accurate centipawn values.

#### `gameManager.ts`
Manages game state for playing against the computer:
- Handles player and computer moves
- Manages Stockfish worker for AI moves
- Tracks game state (check, checkmate, stalemate)
- Configurable difficulty levels

#### `uciParser.ts`
Robust UCI protocol parser that:
- Handles iterative deepening without losing moves
- Parses multi-line analysis (MultiPV)
- Extracts evaluation scores and best moves
- Manages analysis state across depth iterations

#### `moveConversion.ts`
Converts between UCI notation and Standard Algebraic Notation (SAN) for display.

## Installation

```bash
# Clone the repository
git clone https://github.com/RNDev666/eval-guesser-v2.git
cd eval-guesser-v2

# Install dependencies
npm install

# Run development server
npm run dev

# Build for production
npm run build
```

## Usage

### Playing Against Computer
1. Navigate to `/play` or click "Play vs Computer" from homepage
2. Select your color and difficulty level
3. Make moves by clicking and dragging pieces
4. Computer responds automatically based on skill level
5. Use "New Game" to start fresh with new settings

### Analyzing Positions
1. Navigate to `/analysis` or click "Analysis Board"
2. Make moves on the board to explore positions
3. View real-time evaluation and best moves
4. Load custom positions via FEN in the URL parameter
5. Adjust analysis depth for deeper evaluation

### Example Positions
The homepage includes quick links to analyze classic opening positions:
- Italian Game
- Four Knights
- Pirc Defense
- Scotch Game
- Queen's Gambit
- King & Pawn Endgame

## Development

### Project Structure
```
src/
├── lib/
│   ├── EvaluationBar.svelte    # Evaluation display component
│   ├── gameManager.ts           # Game logic for vs computer
│   ├── uciParser.ts             # UCI protocol parser
│   ├── moveConversion.ts        # Move notation converter
│   └── types/
│       └── chess.ts             # TypeScript type definitions
├── routes/
│   ├── +page.svelte            # Homepage
│   ├── play/                   # Play vs computer page
│   └── analysis/               # Analysis board page
└── static/
    ├── stockfish.js            # Stockfish engine
    ├── stockfish.wasm          # WebAssembly binary
    └── stockfish.wasm.js       # WASM loader
```

### Key Features Implemented
- ✅ Real-time chess board with drag-and-drop
- ✅ Stockfish integration via Web Workers
- ✅ UCI protocol parsing with iterative deepening support
- ✅ Evaluation bar with accurate centipawn display
- ✅ Play against adjustable AI (20 skill levels)
- ✅ Position analysis with multi-line support
- ✅ Move history tracking
- ✅ Game state management (check, checkmate, stalemate)
- ✅ FEN position loading
- ✅ Responsive design for all screen sizes

## Contributing

Contributions are welcome! Please feel free to submit issues and pull requests.

## Support

If this project is useful to you, you can support my work on Ko-fi:

[![Support me on Ko-fi](https://ko-fi.com/img/githubbutton_sm.svg)](https://ko-fi.com/rndev666)

## License

MIT

## Credits

- Chess engine: [Stockfish](https://stockfishchess.org/)
- Chess board: [Chessground](https://github.com/lichess-org/chessground)
- Chess logic: [chess.js](https://github.com/jhlywa/chess.js)
- Framework: [SvelteKit](https://kit.svelte.dev/)