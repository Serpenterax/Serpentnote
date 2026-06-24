# Serpentnote - AI Image Prompt Library

**Your personal command center for AI art generation workflows.**

Serpentnote is a powerful visual prompt management tool designed for serious AI artists and content creators. Stop losing track of your best prompts—organize, refine, and reuse them across Stable Diffusion, Midjourney, ComfyUI, and any other AI art generator.

## ✨ What Makes Serpentnote Special

### 🎯 **Channel-Based Organization**
Create themed collections with custom names and emojis—think "Cyberpunk Portraits 🌆", "Fantasy Landscapes 🏔️", or "Product Shots 📸". Each channel stores its own prompts, tags, and reference images.

### 🎨 **Dual Prompt System**
Master prompt engineering with separate **positive prompts** (what you want) and **negative prompts** (what to avoid). Perfect for fine-tuning Stable Diffusion outputs.



### 🏷️ **Smart Tag Library**
Build reusable tag collections that instantly modify prompts without rewriting. Mix and match quality settings, art styles, camera angles, and lighting conditions.

### 🎪 **Danbooru Tag Autocomplete**
Access 650+ professional AI art tags with intelligent autocomplete:
- Quality modifiers: `masterpiece`, `best quality`, `highly detailed`
- Art styles: `anime`, `photorealistic`, `oil painting`, `3d render`
- Lighting: `dramatic lighting`, `golden hour`, `studio lighting`
- Camera angles: `portrait`, `wide shot`, `from below`, `fisheye`
- And much more...



### 📸 **Visual Reference Gallery**
Attach unlimited reference images to each channel. Track what worked, compare variations, and build a visual library of your successful generations.

### ⭐ **Star & Sort System**
Bookmark your best-performing prompts and organize channels with drag-and-drop reordering. Your workflow, your way.

### 💾 **Import/Export Everything**
Backup your entire prompt library or share collections with your team. Perfect for collaboration or migrating between machines.



### 🌍 **Multi-Language Interface**
Work in your preferred language: English, Spanish, French, German, Japanese, or Chinese.

## 🎯 Perfect For

- **AI Artists** building a comprehensive prompt library
- **Content Creators** managing multiple image generation projects
- **Creative Teams** collaborating on AI art workflows
- **Prompt Engineers** experimenting with variations and refinements
- **Anyone** tired of losing track of their best prompts in scattered text files

## 🚀 Getting Started

### Browser Version (Quick Start)
1. Open `index.html` in your browser
2. Everything runs locally—no server required
3. Data stored in browser LocalStorage (5-10MB limit)
4. Perfect for small collections and testing

### Electron Version (Recommended)

**Why Electron?**
- ✅ Unlimited storage capacity
- ✅ Faster performance with large libraries
- ✅ File-based storage—images accessible in your file explorer
- ✅ Desktop app experience with system integration

#### Installation

**Prerequisites:**
- Node.js (v16 or higher)
- npm (comes with Node.js)

**Setup Steps:**

1. **Install dependencies:**
   ```bash
   npm install
   ```

2. **Run in development mode:**
   ```bash
   npm run dev
   ```
   This compiles TypeScript and launches the Electron app.

3. **Build distributable app:**
   ```bash
   npm run package
   ```
   Creates installers in `dist/` folder:
   - **Windows**: `.exe` installer
   - **macOS**: `.dmg` installer
   - **Linux**: `.AppImage` file

**Platform-specific builds:**
```bash
npm run package -- --win   # Windows only
npm run package -- --mac   # macOS only
npm run package -- --linux # Linux only
```

#### First Launch

On first launch, Serpentnote automatically creates a `serpentnote-data` folder in the app's root directory:

```
serpentnote-app/
└── serpentnote-data/
    ├── channels.json           # Channel metadata & prompts
    ├── tags.json              # Your tag library
    ├── customDanbooruTags.json # Custom Danbooru tags
    └── images/                # All uploaded images
        ├── image-1.png
        ├── image-2.jpg
        └── ...
```

**Storage Tips:**
- Images are stored in full quality as separate files
- Your prompt library grows with your creativity—no artificial limits
- Easy to backup: just copy the `serpentnote-data` folder
- Images accessible via file explorer for external editing

## 📖 Usage Guide

### Creating Your First Channel

1. Click the **"+"** button in the sidebar
2. Name your channel (e.g., "Cyberpunk Portraits")
3. Choose an emoji icon (🌆)
4. Write your positive prompt:
   ```
   cyberpunk woman, neon lights, rain, detailed face, futuristic
   ```
5. Add negative prompt:
   ```
   blurry, low quality, distorted, ugly
   ```
6. Add reusable tags: `masterpiece`, `4k`, `dramatic lighting`

### Uploading Reference Images

**Three ways to add images:**

1. **Drag & Drop** - Drag images from your desktop into the gallery area
2. **Click to Upload** - Double-click the gallery area to open file picker
3. **Paste** - Copy an image and paste it directly (Ctrl/Cmd + V)

Images automatically inherit the channel's prompts and tags as metadata.

### Working with Tags

**Create Tag Collections:**
- Click hamburger menu ☰ → "Manage Tags"
- Add tags with emoji support: `✨ masterpiece`, `🎨 oil painting`
- Tags apply to all images in the channel

**Built-in Danbooru Tags:**
- Start typing in the prompt field
- Autocomplete suggests professional AI art tags
- Add custom tags: Settings → "Manage Danbooru Tags"

### Organizing Channels

- **Star Channels** - Click the ⭐ icon to mark favorites
- **Drag to Reorder** - Click and drag channels in the sidebar
- **Filter by Tags** - Use the filter bar to show specific tags
- **Search** - Type to find channels by name or prompt content

### Backup & Restore

**Export Everything:**
1. Click hamburger menu ☰
2. Select "Export All Data"
3. Choose format:
   - **JSON** - Full backup with all metadata
   - **Danbooru** - Tag list for external tools

**Import Data:**
1. Hamburger menu → "Import Data"
2. Select your exported JSON file
3. Data merges with existing library (or replaces if empty)

### Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl/Cmd + N` | New channel |
| `Ctrl/Cmd + E` | Export data |
| `Ctrl/Cmd + Z` | Undo |
| `Ctrl/Cmd + Y` | Redo |
| `Delete` | Delete current image |
| `Esc` | Close modals |

## 🛠️ Troubleshooting

### App won't start
- Verify Node.js: `node --version` (should be v16+)
- Reinstall dependencies: `rm -rf node_modules && npm install`
- Try: `npm run build:js` then `npm start`

### Images not loading
- Check `serpentnote-data/images/` folder exists
- Verify file permissions (should be read/write)
- Look for errors in DevTools (Ctrl+Shift+I)

### Storage Issues
- **Browser version**: Hit LocalStorage limit? Switch to Electron
- **Electron version**: Images stored in `./serpentnote-data/images/`
- Check disk space—large libraries need room to grow

### Clearing Data
Settings → Data Management → "Clear All Data" (warning: irreversible!)

## 🔧 Development

### Project Structure
```
serpentnote/
├── main.ts              # Main app logic (TypeScript)
├── main.js             # Compiled JavaScript
├── index.html          # HTML structure
├── style.css           # All styles
├── electron-main.js    # Electron main process
├── preload.js          # IPC bridge (security)
└── package.json        # Dependencies & scripts
```

### Build Commands
```bash
npm run build:js        # Compile TypeScript
npm run dev            # Dev mode with hot reload
npm start              # Run without recompiling
npm run package        # Build distributable app
```

## 🌐 Technology

**Built with:**
- TypeScript for type safety
- Electron for desktop app
- LocalStorage/File System for data persistence
- Zero backend—complete privacy for your creative work

**No cloud, no tracking, no subscriptions.** Your prompts stay yours.

## 📄 License

MIT License - Free to use, modify, and distribute

## 💖 Credits

- Built with Electron & TypeScript
- Icons from Heroicons
- Emoji rendering by Twemoji
- Danbooru tag database from community contributions

---

**Made with ❤️ for AI artists who take their craft seriously.**
