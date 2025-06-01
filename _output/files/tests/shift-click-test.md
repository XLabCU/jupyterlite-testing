# Shift+Click Wikilink Test

This file tests the new Shift+click functionality for wikilinks in both source and preview modes.

## Test Instructions

### In Preview Mode:
1. **Regular click** on a wikilink opens the file in the current mode (edit or preview)
2. **Shift+click** on a wikilink always opens the file in **source/edit mode**

### In Source Mode:
1. **Shift+click** anywhere within a wikilink (e.g., on `[[` or `]]` or the filename) opens the file in **source/edit mode**
2. **Regular click** does nothing special (normal cursor positioning)

## Test Wikilinks

Try these wikilinks with regular click and Shift+click:

### Existing Files
- [[notes.md]] - should exist in your content directory
- [[start.md]] - should exist in your content directory  
- [[project-ideas.md]] - may exist in your content directory

### Custom Display Names
- [[notes.md|My Notes]] - existing file with custom display
- [[start.md|Getting Started Guide]] - existing file with custom display

### Non-existent Files (for testing creation)
- [[new-research-note]] - will prompt to create new file
- [[meeting-minutes-2024]] - will prompt to create new file
- [[ideas.ipynb]] - will prompt to create new notebook

### Different File Types
- [[data-analysis.ipynb]] - Jupyter notebook (if exists)
- [[sample-data.csv]] - CSV file (if exists)
- [[config.json]] - JSON file (if exists)

## Expected Behavior

### Regular Click (Preview Mode):
- File opens in current view mode (respects the markdown mode toggle)
- If in preview mode → opens in preview
- If in edit mode → opens in edit mode

### Shift+Click (Both Modes):
- File **always** opens in **source/edit mode**
- Useful for quickly jumping to edit a linked file
- Works in both preview and source views

### Source Mode Shift+Click:
- Click anywhere within the wikilink syntax: `[[filename]]`
- Can click on the brackets, filename, or custom display text
- Opens the target file directly in edit mode

## Test Scenarios

1. **Open this file in preview mode**
   - Regular click on [[notes.md]] 
   - Shift+click on [[notes.md]]
   - Notice the difference in how the file opens

2. **Open this file in source mode**
   - Shift+click on any wikilink in the source
   - The target file should open in edit mode

3. **Test broken links**
   - Shift+click on [[non-existent-file]]
   - Should prompt to create the file
   - If created, opens in edit mode

4. **Test different file types**
   - Shift+click on [[new-notebook.ipynb]]
   - Should create and open a new notebook

## Usage Tips

- **Shift+click** is perfect for quick editing workflows
- Use it when you want to immediately edit a linked file
- Especially useful when browsing in preview mode but need to edit
- Works with file creation - new files open in edit mode automatically

This feature makes navigation between notes much more efficient for content creation and editing! ⚡