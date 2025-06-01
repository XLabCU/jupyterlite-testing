# Path-Aware Backlinks Test

This file tests the enhanced backlinks functionality that now handles duplicate filenames in different folders correctly.

## Problem Solved

### **Before (Broken)**:
```
content/
├── notes/analysis.md     ← Contains [[summary]]
└── projects/analysis.md  ← Contains [[summary]]
```

When viewing `summary.md`, backlinks would incorrectly show BOTH `analysis.md` files, even though only one actually links to the current file.

### **After (Fixed)**:
- **Path resolution**: Wikilinks are resolved to actual file paths
- **Precise matching**: Only shows backlinks from files that actually reference the current file
- **Duplicate filename support**: Handles multiple files with same name in different folders

## Test Scenario

Create this folder structure to test the fix:

```
content/
├── path-aware-backlinks-test.md (this file)
├── summary.md
├── notes/
│   ├── analysis.md
│   └── research.md
├── projects/
│   ├── analysis.md (same filename as notes/analysis.md)
│   └── data.ipynb
└── archive/
    └── analysis.md (same filename again!)
```

## Test Files to Create

### 1. **Top-level**: `summary.md`
```markdown
# Summary

This is the target file that should show backlinks.
```

### 2. **First analysis file**: `notes/analysis.md`
```markdown
# Notes Analysis

This file links to [[summary]] and [[research.md]].
Based on findings in [[summary.md]].
```

### 3. **Second analysis file**: `projects/analysis.md`  
```markdown
# Project Analysis

This file does NOT link to summary.
Works with [[data.ipynb]] for project analysis.
```

### 4. **Third analysis file**: `archive/analysis.md`
```markdown
# Archive Analysis

Old analysis that references [[summary]] from the archive.
Historical data from [[summary.md]].
```

### 5. **Research file**: `notes/research.md`
```markdown
# Research Notes

Research data that feeds into [[summary]].
```

### 6. **Data notebook**: `projects/data.ipynb`
```markdown
# Data Analysis Notebook

Results will be summarized in [[summary.md]].
```

## Expected Behavior

### When viewing `summary.md`:
**Should show backlinks from**:
- ✅ `notes/analysis.md` (contains `[[summary]]` and `[[summary.md]]`)
- ✅ `archive/analysis.md` (contains `[[summary]]` and `[[summary.md]]`)  
- ✅ `notes/research.md` (contains `[[summary]]`)
- ✅ `projects/data.ipynb` (contains `[[summary.md]]`)

**Should NOT show backlinks from**:
- ❌ `projects/analysis.md` (doesn't link to summary)

### Console Output Should Show:
```
Backlinks: Found wikilink in notes/analysis.md: [[summary]] -> target: "summary"
Backlinks: Resolved "summary" to path: "summary.md"
Backlinks: Checking against current file path: "summary.md"
Backlinks: FOUND MATCH! Adding backlink

Backlinks: Found wikilink in projects/analysis.md: [[data.ipynb]] -> target: "data.ipynb"
Backlinks: Resolved "data.ipynb" to path: "projects/data.ipynb"  
Backlinks: Checking against current file path: "summary.md"
(No match - correctly excluded)
```

## Advanced Test Cases

### 1. **Ambiguous References**
If you have:
- `notes/config.json`
- `projects/config.json`

And a wikilink `[[config.json]]`, the system will:
- Find the first matching file (implementation dependent)
- Only show backlinks for the file that actually gets resolved

### 2. **Extension Handling**
- `[[summary]]` → resolves to `summary.md`
- `[[data.ipynb]]` → resolves to `projects/data.ipynb`  
- `[[summary.md]]` → resolves to `summary.md`

### 3. **Cross-Folder References**
Files in any folder can reference files in any other folder, and backlinks will correctly resolve the actual target.

## Testing Instructions

1. **Create the test folder structure** as shown above
2. **Add the content** to each file as specified
3. **Open `summary.md`** in any mode (edit/preview)
4. **Open backlinks panel** (`Alt+B`)
5. **Verify correct backlinks** are shown
6. **Check console logs** to see path resolution in action
7. **Test with other files** to ensure consistent behavior

## Success Criteria

✅ **Only correct backlinks shown** - no false positives from duplicate filenames
✅ **Path resolution works** - console shows proper path resolution
✅ **All folders searched** - finds backlinks from any directory depth
✅ **Mixed file types** - works with .md, .ipynb files
✅ **Extension handling** - properly handles with/without extensions

## Troubleshooting

If you see incorrect backlinks:

1. **Check console logs** - verify path resolution is working
2. **Verify wikilink syntax** - ensure proper `[[filename]]` format
3. **Check file existence** - ensure target files actually exist
4. **Test step by step** - start with simple cases, add complexity

This fix ensures your PKM system works correctly even with complex folder structures and duplicate filenames! 📁🎯