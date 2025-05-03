// README.md
# 🧠 SATD Helper Extension for VS Code

This VS Code extension helps developers monitor Self-Admitted Technical Debt (SATD) in Git repositories and identifies opportunities to repay technical debt when pull requests are merged.

## 🚀 Features

- 🔍 **Git Repository Monitoring**: Scans commit history to identify self-admitted technical debt (TODO, FIXME, etc.)
- 🔄 **PR Merge Detection**: Automatically detects when pull requests are merged
- 💡 **Repayment Opportunities**: Uses AI to identify opportunities to pay off technical debt based on merged changes
- 📊 **Visual Reporting**: Shows webview panels with detailed SATD information and repayment opportunities  
- 🔔 **Real-time Notifications**: Alerts you when changes might address existing technical debt
- ⚙️ **Configurable Settings**: Customize scan intervals, keywords, and relevance thresholds

## 🛠️ Architecture

The extension follows a professional, modular architecture with clear separation of concerns:

```
src/
├── extension.ts              # Entry point
├── models/                   # Data models
│   ├── satdItem.ts
│   └── repaymentOpportunity.ts
├── services/                 # Core services
│   ├── gitService.ts
│   └── openAIService.ts
├── monitors/                 # Monitoring components
│   └── satdMonitor.ts
├── processors/              # Processing components
│   └── prProcessor.ts
├── repositories/            # Data storage
│   ├── baseRepository.ts
│   ├── satdRepository.ts
│   └── repaymentRepository.ts
├── analyzers/               # Analysis components
│   └── opportunityAnalyzer.ts
├── parsers/                 # Parsing utilities
│   └── satdParser.ts
├── managers/                # UI management
│   ├── statusBarManager.ts
│   ├── notificationManager.ts
│   └── webviewManager.ts
├── webviews/                # Webview providers
│   └── opportunityWebviewProvider.ts
├── config/                  # Configuration
│   └── configManager.ts
└── utils/                   # Utilities
    └── logger.ts
```

## 🚀 Quick Start

### Prerequisites

- VS Code 1.63.0 or higher
- Node.js 16.x or higher
- OpenAI API key
- Git repository

### Installation

1. Clone the repository
```bash
git clone https://github.com/yourusername/satd-helper-extension.git
cd satd-helper-extension
```

2. Install dependencies
```bash
npm install
```

3. Configure OpenAI API key
```bash
echo "OPENAI_API_KEY=your-openai-key" > .env
```

4. Build the extension
```bash
npm run compile
```

5. Launch in VS Code
- Press `F5` to open a new Extension Development Host window
- Or run: `code --extensionDevelopmentPath=/path/to/satd-helper-extension`

## 📝 Usage

### Monitoring Technical Debt

The extension automatically:
- Scans your git repository for SATD comments (TODO, FIXME, HACK, etc.)
- Displays the count in the status bar (bottom-left)
- Click the status bar item to refresh the scan

### Configuration

Configure the extension through VS Code settings:

```json
{
  "satd-helper.scanInterval": 60000,     // Scan interval in ms
  "satd-helper.prCheckInterval": 30000,  // PR check interval in ms
  "satd-helper.relevanceThreshold": 0.7, // Relevance threshold for AI
  "satd-helper.satdKeywords": [          // Keywords to identify SATD
    "TODO", "FIXME", "HACK", "XXX", "BUG"
  ]
}
```

### PR Merge Detection

When a pull request is merged:
1. The extension detects the merge commit
2. Analyzes changed files for relevance to existing SATD
3. Shows notifications for potential repayment opportunities
4. Click notification to view detailed analysis

## 🤖 How It Works

### Components

1. **SATDMonitor**: Scans git history for technical debt patterns
2. **PRProcessor**: Detects and analyzes PR merges
3. **OpportunityAnalyzer**: Uses AI to match SATD with code changes
4. **Repositories**: Persist SATD items and opportunities
5. **UI Managers**: Handle status bar, notifications, and webviews

### AI Analysis

- Uses OpenAI GPT to classify SATD and analyze relevance
- Generates relevance scores for PR changes
- Provides actionable explanations

## 🧪 Development

### Scripts

```bash
npm run compile    # Compile TypeScript
npm run watch     # Watch for changes
npm run lint      # Run ESLint
npm run format    # Format with Prettier
npm test          # Run tests
```

### Testing

```bash
# Run tests
npm test

# Run with specific test file
npm test -- path/to/test.ts
```

## 📦 Dependencies

### Runtime
- `vscode`: VS Code extension API
- `simple-git`: Git operations
- `openai`: GPT integration for SATD analysis
- `dotenv`: Environment variable management

### Development
- `typescript`: Static typing
- `eslint`: Code linting
- `prettier`: Code formatting
- `@types/*`: TypeScript definitions

## 🔒 Security

- API keys are stored in `.env` file (not committed)
- No sensitive data is sent to external services beyond OpenAI API
- All credentials are handled securely

## 🚀 Roadmap

- [ ] GitHub API integration for PR information
- [ ] Team collaboration features
- [ ] Automated SATD resolution suggestions
- [ ] Integration with issue tracking systems
- [ ] Custom AI model training for specific projects

## 📄 License

MIT License