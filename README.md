# ⚡ AI Tools Directory

![Dashboard Preview](assets/dashboard_preview.png)

A lightweight, high-performance, single-page dashboard designed to organize and search through hundreds of curated AI-powered tools. 

The directory syncs directly from an upstream data source and provides an incredibly fast and fluid user experience with a sleek Cyberpunk/Matrix-inspired interface.

## 🚀 Features

- **Blazing Fast**: Zero-dependency frontend, entirely vanilla HTML/CSS/JS. Total payload well under the 200KB limit.
- **Dynamic Theming**: Includes a striking "Matrix" default theme, along with alternative "Midnight" and "Ocean" themes. 
- **Automated Upstream Syncing**: Integrates seamlessly with GitHub actions (`.github/automation.yaml`) to pull and update the markdown database from the upstream `Top-AI-Tools` repository.
- **Category Navigation**: Automatically categorizes tools into an intuitive sidebar navigation with item counts.
- **Instant Search**: Search through hundreds of AI tools instantly with optimized debounced filtering.
- **Expand All Descriptions**: Quickly toggle all tool descriptions using the Expand/Collapse button in the header.
- **Responsive Design**: Beautiful interface whether on a desktop monitor or a mobile screen. 

## 🛠 Project Structure

- `index.html`: The core frontend application. Handles markdown parsing, rendering, and UI interactions.
- `sync.py`: A python script that acts as the daemon to fetch `tools.md` from the upstream repo and process it locally.
- `.github/`: Contains workflow automation scripts and mapping variables to synchronize data consistently.
- `assets/`: Contains screenshots and visual assets.

## 💻 Getting Started

To run the project locally, you only need to serve the directory.

```bash
# Clone the repository
git clone https://github.com/mdnaimul22/ai-tools.git

# Serve the directory
cd ai-tools
python3 -m http.server 8080
```
Open `http://localhost:8080` in your browser.

## 🔄 Updating Data

To manually sync and pull the latest AI tools from the upstream database:
```bash
python3 sync.py
```
*Note: Make sure you have `PyYAML` installed (`pip install pyyaml`) if you plan to run the synchronization script.*
