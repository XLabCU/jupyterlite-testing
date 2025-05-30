# Welcome to PKM Extension Demo

This is the main entry point for testing the Personal Knowledge Management extension features.

## Features to Test

### 1. Wikilinks
- Basic link: [[notes]]
- Link with display text: [[project-ideas|My Project Ideas]]
- Link to research: [[research-methods]]
- Link to daily note: [[2024-01-15]]

### 2. Mode Switching
Press **Alt+M** to toggle between edit and preview modes. The mode should persist when switching between files.

### 3. Backlinks Panel
Press **Alt+B** to open the backlinks panel. It should show which notes link to this file.

**Currently, it is only showing backlinks for materials at the same level**. 

Incidentally, also shows backlinks in markdown blocks in ipynb files (at the same level).

### 4. Search
Press **Alt+F** to search across all markdown files and notebooks.

### 5. File Types
Links work with multiple file types:
- Markdown: [[notes]]
- CSV data: [[sample-data.csv]]
- JSON config: [[config.json]]
- Notebook: [[analysis.ipynb]]

## Getting Started

1. Open this file in **preview mode** (Alt+M)
2. Click on the wikilinks to navigate between notes
3. Try opening the backlinks panel (Alt+B) 
4. Create new notes by clicking on non-existent links
5. Search for content across all files (Alt+F)

## Network of Notes

This demo includes several interconnected notes:
- [[notes]] - General note-taking examples
- [[project-ideas]] - Ideas for future projects  
- [[research-methods]] - Research methodology notes
- [[2024-01-15]] - Daily journal entry
- [[meeting-notes]] - Meeting documentation

Start exploring by clicking any of the links above!