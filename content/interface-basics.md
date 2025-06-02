# Interface Basics: Mastering Your Digital Humanities Toolkit

This tutorial covers all the essential features you'll use daily in your digital humanities work. Think of this as learning the "grammar" of your new research environment.

## Core Navigation Skills

### File Management
- **Create new files**: Click any red wikilink or use File → New
- **Open existing files**: Click blue wikilinks or use the file browser  
- **Save files**: Auto-saves every 30 seconds (or Ctrl/Cmd+S)
- **Rename files**: Right-click in file browser

### View Modes
Every markdown file has two modes:

**Preview Mode** (default):
- Shows formatted text, like reading a webpage
- Wikilinks are clickable
- Best for reading and following connections

**Edit Mode**: 
- Shows raw markdown syntax
- Type here to write and edit
- See the "code" behind the formatting

**Switch modes**: `Alt+M` or click the floating button

## The Four Essential Shortcuts

### 1. Mode Toggle (`Alt+M`)
Switch between reading and writing modes instantly.

**Practice**: 
- Press `Alt+M` now to see this file's markdown
- Notice how `# Interface Basics` creates the heading
- Press `Alt+M` again to return to preview

### 2. Global Search (`Alt+F`)
Search across ALL your notes and notebooks simultaneously.

**Practice**:
- Press `Alt+F` 
- Search for "digital humanities"
- Notice how results show context and file locations
- Click any result to jump to that file

### 3. Backlinks Panel (`Alt+B`)
See which files link TO the current file. This reveals unexpected connections.

**Practice**:
- Press `Alt+B` to open the backlinks panel
- You should see [[getting-started-tutorial]] listed (it links here)
- Click the backlink to jump to that file
- Close and reopen the panel to refresh it

### 4. Link Following (`Ctrl/Cmd+Click`)
Follow wikilinks without losing your place.

**Practice**:
- Hold Ctrl (or Cmd on Mac) and click [[what-is-pkm]]
- The link opens in a new tab
- Use browser tabs to work with multiple files

## Advanced Features

### Auto-completion
When typing wikilinks, the system helps you:

1. Type `[[` (two opening brackets)
2. Start typing a filename
3. Use ↑/↓ arrows to navigate suggestions
4. Press Enter or Tab to complete
5. Type `]]` to close the link

**Try it**: In edit mode, type `[[start` and watch the suggestions appear.

### File Types
You can link to various file types:

- **Markdown notes**: `[[my-note]]` 
- **Jupyter notebooks**: `[[analysis.ipynb]]`
- **Data files**: `[[dataset.csv]]`
- **Config files**: `[[config.json]]`

### Embedding Content

Beyond simple links, you can embed content from other files:

**Block embedding**:
- `![[note-name#heading]]` - Embed a specific section
- `![[note-name#block-id]]` - Embed marked content

**Notebook cell embedding**:
- `![[notebook.ipynb#cell:5]]` - Embed code and output
- `![[notebook.ipynb#cell:5:code]]` - Just the code
- `![[notebook.ipynb#cell:5:output]]` - Just the results

## Organizing Your Workspace

### File Naming Conventions
Good filenames help both humans and systems:

- **Use descriptive names**: `renaissance-art-networks` not `file1`
- **Use hyphens for spaces**: `digital-humanities-methods` 
- **Be consistent**: Pick a pattern and stick to it
- **Include dates when relevant**: `2024-03-15-class-notes`

### Folder Strategy
Start simple, organize later:

- Begin with files in the main directory
- Create folders when you have 10+ related files
- Don't over-organize early - let structure emerge

## Troubleshooting

### Common Issues

**Wikilink not working?**
- Check spelling and capitalization
- Ensure proper `[[double brackets]]`
- Remember file extensions for notebooks: `[[analysis.ipynb]]`

**Auto-completion not appearing?**
- Make sure you're in edit mode
- Type `[[` and pause briefly
- Clear browser cache if persistent

**Backlinks not updating?**
- Close and reopen the backlinks panel (`Alt+B` twice)
- The panel updates when you switch focus to different files

### Getting Help

If something isn't working:
1. Check the browser console (F12) for error messages
2. Try refreshing the page
3. Make sure you're in the right mode (edit vs preview)

## Practice Exercise

Test your skills by completing these tasks:

1. **Navigation**: Open [[what-is-pkm]] using `Ctrl/Cmd+Click`
2. **Search**: Use `Alt+F` to find all mentions of "knowledge"
3. **Backlinks**: Check what links to [[start]] using `Alt+B`
4. **Creation**: Make a new note called [[interface-practice]] and write one sentence about what you learned
5. **Linking**: From your new note, create a link back to this tutorial

## Next: Understanding PKM

Once you're comfortable with these basics, continue to [[what-is-pkm]] to understand the theory behind these practices.

---

**Remember**: Fluency with these tools isn't just about efficiency - it changes how you think about research, writing, and knowledge creation in the digital humanities.

**Navigation**: [[getting-started-tutorial]] ← Previous | Next → [[what-is-pkm]]