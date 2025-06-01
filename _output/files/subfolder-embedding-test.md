# Block Embedding Path Resolution Test

This file tests that block embedding now works correctly when files are in subfolders.

## Test Overview

The issue was that block embedding worked when files were at the top level, but failed when files were moved into subfolders. This has been fixed with proper path resolution.

## What Was Fixed

### Before (Broken):
- Block embedding used filename directly: `![[embedding-source.md#Introduction]]`
- When files were in subfolders, the system couldn't find them
- Error: `Block not found` even when the file existed

### After (Fixed):
- Block embedding now uses `findFile()` to search across all directories
- Resolves relative paths correctly regardless of folder structure
- Works with any level of nested directories

## Test Instructions

1. **Create a subfolder structure** in your content directory:
   ```
   content/
   ├── subfolder-embedding-test.md (this file)
   ├── notes/
   │   ├── research-notes.md
   │   └── methodology.md
   └── projects/
       ├── project-alpha.md
       └── data/
           └── analysis-notes.md
   ```

2. **Test cross-folder embedding** from this top-level file:

## Cross-Folder Block Embeds

### From notes/ subfolder:
![[research-notes.md#Key Findings]]

![[methodology.md#Data Collection]]

### From projects/ subfolder:
![[project-alpha.md#Overview]]

### From nested projects/data/ subfolder:
![[analysis-notes.md#Results]]

## Expected Behavior

✅ **All embeds should work** regardless of:
- Source file location (top-level, subfolder, nested subfolder)
- Target file location (any directory level)
- Relative paths between source and target

✅ **Console output should show**:
```
Block embedding - searching for file: research-notes.md -> target: research-notes.md
Block embedding - searching in directory: root, found X items
Block embedding - found match: notes/research-notes.md
Block embedding - resolved "research-notes.md" to "notes/research-notes.md"
```

## Test Files to Create

Create these test files to verify the fix:

### notes/research-notes.md
```markdown
# Research Notes

## Key Findings

Our research shows significant improvements in user engagement when implementing the new interface design. Users reported 40% higher satisfaction rates.

## Methodology

The study was conducted over 6 weeks with 200 participants across different demographics.
```

### notes/methodology.md
```markdown
# Research Methodology

## Data Collection

We used a mixed-methods approach combining quantitative surveys and qualitative interviews to gather comprehensive insights.
```

### projects/project-alpha.md
```markdown
# Project Alpha

## Overview

Project Alpha is a comprehensive study on user interface improvements for mobile applications. The project spans 12 weeks and involves multiple research phases.
```

### projects/data/analysis-notes.md
```markdown
# Data Analysis Notes

## Results

The statistical analysis reveals significant correlations between interface design elements and user satisfaction metrics (p < 0.05).
```

## Advanced Test Scenarios

### 1. Bi-directional embedding
- File in subfolder embedding from top-level
- Top-level file embedding from subfolder
- Subfolder-to-subfolder embedding

### 2. Deep nesting
- Files in deeply nested directories (3+ levels)
- Cross-references between different branches

### 3. File types
- .md files in subfolders
- .ipynb files in subfolders
- Mixed file types across directories

## Success Criteria

✅ All block embeds render correctly with content
✅ No "Block not found" errors in console
✅ File resolution logs show correct path discovery
✅ Works regardless of current file location
✅ Works regardless of target file location

This fix ensures that your PKM system works seamlessly with any folder organization! 📁✨