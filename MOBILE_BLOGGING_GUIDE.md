# Mobile Blogging Guide 📱

## Obsidian + Git Setup for Travel Blogging

### Why Obsidian is Perfect for Mobile Blogging:
- ✅ **Live preview** - See exactly how your post will look
- ✅ **Switch between edit/preview** with one tap
- ✅ **Rich Markdown editor** with formatting buttons
- ✅ **Photo insertion** directly from camera/gallery
- ✅ **Works offline** - write anywhere, sync when you have WiFi
- ✅ **Git integration** for automatic backups and publishing

### Step-by-Step Setup

#### 1. Install Required Apps
- **Obsidian** (from Google Play Store)
- **Obsidian Git Plugin** (install from Community Plugins)

#### 2. Clone Repository to Phone

**Option A: Using Obsidian Git Plugin (Recommended)**
1. Open Obsidian
2. Tap "Create new vault"
3. Choose "Create vault from folder" 
4. Enable Community Plugins (Settings → Community Plugins)
5. Install "Obsidian Git" plugin
6. Run command: "Obsidian Git: Clone an existing remote repo"
7. Enter your GitHub repository URL: `https://github.com/yourusername/TravelBlog.git`
8. **Clone location**: Usually `/storage/emulated/0/Documents/TravelBlog/` or similar
9. Set this folder as your Obsidian vault

**Option B: Using Termux (for advanced users)**
1. Install Termux from F-Droid
2. Run: `pkg install git`
3. Navigate to desired location: `cd /storage/emulated/0/Documents/`
4. Clone: `git clone https://github.com/yourusername/TravelBlog.git`
5. **Clone location**: `/storage/emulated/0/Documents/TravelBlog/`
6. Point Obsidian vault to this folder

**Typical Android Storage Locations:**
- **Internal Storage**: `/storage/emulated/0/`
- **Documents Folder**: `/storage/emulated/0/Documents/`
- **Downloads Folder**: `/storage/emulated/0/Download/`
- **Obsidian Default**: `/storage/emulated/0/Documents/ObsidianVaults/`

**Important Notes:**
- Choose a location you can easily find in file managers
- Avoid system folders or app-specific directories
- Make sure the location has enough storage space
- The folder will contain your entire blog repository

#### 3. Configure Obsidian Git
- Set auto-commit interval (e.g., every 30 minutes)
- Configure commit message template: "Mobile post: {{date}}"
- Enable auto-push when online

### Quick Posting Workflow

#### Creating a New Post:
1. **Open Obsidian** on your phone
2. **Navigate to `_posts` folder**
3. **Create new note** with filename: `YYYY-MM-DD-post-title.md`
4. **Use template below** or copy from `_TEMPLATE.md`
5. **Switch to preview mode** to see how it looks
6. **Add photos** by dragging from gallery or using attachment button
7. **Commit & push** using Obsidian Git plugin

#### Daily Blogging Template:

```markdown
---
title: "Day X in [City Name]"
layout: post
date: 2025-MM-DD
categories: travel
country: "Country Name"
---

![Main photo](../assets/images/mobile/2025-MM-DD-main.jpg)

Quick summary of today's adventures in one or two sentences.

## Morning
What I did this morning, where I went, what I saw.

## Afternoon  
Afternoon activities, sights, experiences.

## Evening
Dinner, nightlife, or relaxing activities.

## Food Highlights
- **Breakfast**: What and where
- **Lunch**: Description and location  
- **Dinner**: Restaurant and dishes

## Photos of the Day
![Activity photo](../assets/images/mobile/2025-MM-DD-activity.jpg)
*Caption describing what's happening*

![Food photo](../assets/images/mobile/2025-MM-DD-food.jpg)
*What you're eating and where*

## Tomorrow's Plan
Brief note about what you're planning for tomorrow.

---
*Posted from [Current Location] 📍*
```

### Obsidian Mobile Tips

#### Switching Views:
- **Edit Mode**: Tap pencil icon - see raw Markdown
- **Preview Mode**: Tap eye icon - see formatted result  
- **Live Preview**: Best of both - edit with live formatting

#### Adding Photos:
1. **Drag & Drop**: From gallery directly into editor
2. **Attachment Button**: Use paperclip icon in toolbar
3. **Camera**: Take photo directly from Obsidian
4. **Auto-resize**: Obsidian can automatically resize large photos

#### Formatting Shortcuts:
- **Bold**: Select text + Ctrl+B (or formatting toolbar)
- **Italic**: Select text + Ctrl+I
- **Headers**: Use # ## ### or formatting buttons
- **Links**: [Text](URL) or use link button

### Git Operations on Mobile

#### Quick Commands:
- **Commit**: Obsidian Git: Commit all changes
- **Push**: Obsidian Git: Push  
- **Pull**: Obsidian Git: Pull (to get updates from other devices)
- **Auto-sync**: Enable in plugin settings for hands-free operation

#### Commit Message Templates:
- "Day 1 in Paris - Morning exploration"
- "Added photos from Louvre visit"
- "Quick evening update from cafe"
- "Travel day: Paris to Amsterdam"

### Offline Writing Strategy

1. **Write throughout the day** without worrying about internet
2. **Take lots of photos** - organize later
3. **Use voice-to-text** for quick notes while walking
4. **Sync when you have WiFi** at hotel/cafe
5. **Keep posts short and frequent** rather than one long post

### Photo Management Tips

#### File Naming Convention:
- `YYYY-MM-DD-description.jpg`
- Example: `2025-08-15-eiffel-tower.jpg`

#### Size Optimization:
- Obsidian can auto-resize to web-friendly sizes
- Recommended: Max 1920px width for fast loading
- Use compression for mobile data savings

### Troubleshooting

#### Common Issues:
- **Sync conflicts**: Pull before making changes
- **Large files**: Compress photos before uploading  
- **No internet**: Write offline, sync later
- **Battery drain**: Disable auto-sync when battery low

#### Backup Strategy:
- Obsidian Git automatically backs up to GitHub
- Keep local copies on phone storage
- Export important posts to other apps if needed

### Finding Your Cloned Repository

#### Using File Manager:
1. Open your phone's **File Manager** app
2. Navigate to **Internal Storage** (or "Phone" storage)
3. Look for **Documents** folder
4. Find **TravelBlog** folder (or whatever you named it)
5. This contains your entire blog repository

#### Repository Structure on Phone:
```
TravelBlog/                    ← Your vault root
├── _posts/                    ← Your blog posts go here
│   ├── 2024-12-15-paris.md
│   └── _TEMPLATE.md
├── _layouts/
├── _includes/
├── assets/
│   └── images/
│       └── mobile/            ← Upload photos here
├── _config.yml
└── .git/                      ← Git tracking (hidden)
```

#### Setting Up Obsidian Vault:
1. **Open Obsidian**
2. **Tap "Open folder as vault"**
3. **Navigate to your cloned TravelBlog folder**
4. **Select the root folder** (contains _posts, _config.yml, etc.)
5. **Now Obsidian will treat this as your vault**

#### Working with Posts:
- **Navigate to `_posts` folder** in Obsidian
- **Create new notes** with `.md` extension
- **Use proper filename format**: `YYYY-MM-DD-post-title.md`
- **Photos go in**: `assets/images/mobile/`

### Storage Considerations

#### Space Requirements:
- **Basic repository**: ~50-100 MB
- **With photos**: Can grow to several GB
- **Recommend**: Keep at least 2GB free space
- **Tip**: Regularly push photos to remove from local storage if needed

#### Backup Locations:
- **Primary**: GitHub repository (automatically synced)
- **Local**: Phone internal storage  
- **Optional**: Cloud backup apps can sync the folder

---

Happy travels! 🌍✈️
