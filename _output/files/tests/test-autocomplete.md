# Test Autocomplete

This file is for testing the wikilink autocomplete functionality.

## Testing .md files
Try typing `[[` followed by letters to see if markdown files appear:
- Should show files like: start, glossary, etc.

## Testing .ipynb files  
Try typing `[[` followed by letters to see if notebook files appear:
- Should show files like: python.ipynb, javascript.ipynb, altair.ipynb, etc.

## Test Cases

1. Type `[[p` - should show files starting with 'p' like python.ipynb, p5.ipynb
2. Type `[[start` - should show start.md 
3. Type `[[alt` - should show altair.ipynb
4. Type `[[DH ` - should show DH-related markdown files

The autocomplete should:
- Show both .md and .ipynb files
- Include file extension for .ipynb files only
- Be navigable with arrow keys
- Be insertable with Enter or Tab
- Closeable with Escape