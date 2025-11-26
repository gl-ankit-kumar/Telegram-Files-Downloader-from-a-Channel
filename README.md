# Telegram Channel Downloader (Jupyter GUI)

[![Python](https://img.shields.io/badge/python-3.10%2B-blue)]()
[![License: MIT](https://img.shields.io/badge/license-MIT-green)]()
[![Jupyter](https://img.shields.io/badge/Jupyter-GUI-orange)]()

A robust, notebook-first Telegram channel downloader with an interactive GUI. Scan channels via invite links, select PDFs and videos, and download them with real-time progress tracking, speed indicators, and checkpoint-based resume functionality.

## Features

- 🖥️ **Interactive Jupyter GUI** built with ipywidgets
- 🔐 **Secure login flow** with session persistence
- 📁 **Smart file detection** for PDFs, MP4s, and documents
- 📊 **Real-time progress** with per-file and overall progress bars
- 🚀 **Download speed indicators** and transfer statistics
- 💾 **Checkpoint system** to resume downloads and skip completed files
- 🎯 **Direct file writes** (no .part files)
- 🔄 **Sequential downloads** for reliability and FloodWait avoidance
- 📝 **Filename sanitization** and path safety

## Quick Start

### Prerequisites

- Python 3.10+
- Telegram API credentials ([get them here](https://my.telegram.org))

### Installation

1. **Clone and setup environment:**
```bash
git clone <your-repo-url>
cd telegram-downloader

# Create conda environment (recommended)
conda create -n tg_gui python=3.11
conda activate tg_gui

# Or use virtualenv
python -m venv tg_gui_env
source tg_gui_env/bin/activate  # Linux/Mac
# OR
tg_gui_env\Scripts\activate    # Windows
```

2. **Install dependencies:**
```bash
pip install -r requirements.txt
```

3. **Configure your API credentials:**
   - Set environment variables:
     ```bash
     export TG_API_ID=your_api_id
     export TG_API_HASH=your_api_hash
     ```
   - Or edit the configuration section in the notebook

4. **Launch JupyterLab:**
```bash
jupyter lab
```

### Usage

1. Open `telegram_downloader_gui.ipynb` in JupyterLab
2. **First-time setup:**
   - Enter your phone number and click "Send code"
   - Enter the verification code received via Telegram
   - Complete 2FA if enabled
3. **Download files:**
   - Paste channel invite link in `INVITE_LINK` variable
   - Click "Refresh list" to scan the channel
   - Select files from the list
   - Click "Start download" to begin transfer

Files are saved to `~/Desktop/telegram_downloads/` by default.

## Project Structure

```
telegram-downloader/
├── telegram_downloader_gui.ipynb  # Main GUI notebook
├── requirements.txt               # Python dependencies
├── README.md                     # This file
├── .gitignore                    # Git ignore rules
└── downloaded_gui_checkpoint.json # Download progress (auto-generated)
```

## Configuration

### Environment Variables
- `TG_API_ID`: Your Telegram API ID
- `TG_API_HASH`: Your Telegram API Hash

### Notebook Variables
- `INVITE_LINK`: Channel invite link or username
- `OUTDIR`: Output directory (default: `~/Desktop/telegram_downloads`)
- `SESSION`: Session file prefix for authentication persistence

### Common Issues

**Login failures:**
- Ensure phone number includes country code
- Check internet connection
- Verify API credentials are correct

**Download issues:**
- Check available disk space
- Ensure channel is accessible
- Verify file permissions in output directory

**Widget display problems:**
```bash
jupyter labextension install @jupyter-widgets/jupyterlab-manager
jupyter lab build
```

### Performance Tips
- Use sequential downloads to avoid FloodWait errors
- Keep output directory path short (especially on Windows)
- Monitor disk space for large video files

## Security Notes

- Session files contain authentication tokens - keep them secure
- Never commit API keys or session files to version control
- Consider using a dedicated Telegram account for downloading


## Contributing

Contributions welcome! Please:
1. Fork the repository
2. Create a feature branch
3. Submit a pull request with clear description

## Support

For issues and questions:
1. Check the troubleshooting section above
2. Review Telethon documentation for API-related issues
3. Open a GitHub issue with detailed description
```
