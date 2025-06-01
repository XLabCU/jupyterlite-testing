# Backlinks Test - Improved Functionality

This file tests the enhanced backlinks functionality that now properly handles:
1. **All folder structures** - searches recursively through all directories
2. **Jupyter notebooks** - properly handles .ipynb files with extensions
3. **Consistent behavior** - shows backlinks for the currently focused file

## Test Overview

### What Was Fixed:

#### 1. **File Extension Handling**
- **Before**: Inconsistent handling of .ipynb vs .md files
- **After**: Always uses full filename with extension for .ipynb files
- **Backward compatibility**: Still supports .md files referenced without extension

#### 2. **Wikilink Matching Logic**
- **Enhanced matching** supports:
  - `[[notebook.ipynb]]` → matches `notebook.ipynb`
  - `[[markdown-note]]` → matches `markdown-note.md`
  - `[[markdown-note.md]]` → matches `markdown-note.md`

#### 3. **Folder Structure Support**
- **Recursive search** through all directories and subdirectories
- **Cross-folder backlinks** work correctly
- **Any nesting level** supported

## Test Instructions

### Setup Test Files:

Create these files to test backlinks functionality:

#### 1. **Top-level file**: `notes.md`
```markdown
# Research Notes

Links to notebooks: [[data-analysis.ipynb]] and [[visualization.ipynb]]
Links to other notes: [[methodology]] and [[findings.md]]
```

#### 2. **Subfolder file**: `projects/analysis.md`
```markdown
# Analysis

Based on [[notes.md]] and using [[data-analysis.ipynb]]
See also [[findings.md]] for results.
```

#### 3. **Jupyter notebook**: `notebooks/data-analysis.ipynb`
```markdown
# Data Analysis

This analysis references [[notes.md]] and will be used by [[analysis.md]].
Results stored in [[findings.md]].
```

#### 4. **Deep nested**: `projects/research/findings.md`
```markdown
# Findings

Data from [[data-analysis.ipynb]] shows interesting patterns.
Methodology described in [[notes.md]].
```

### Testing Procedure:

1. **Open the backlinks panel** (`Alt+B`)

2. **Test markdown files**:
   - Open `notes.md` → should show backlinks from `analysis.md` and `data-analysis.ipynb`
   - Open `methodology.md` → should show backlinks from `notes.md`

3. **Test Jupyter notebooks**:
   - Open `data-analysis.ipynb` → should show backlinks from `notes.md`, `analysis.md`, and `findings.md`
   - Verify that wikilinks like `[[data-analysis.ipynb]]` are properly detected

4. **Test cross-folder functionality**:
   - Open files in different folders
   - Verify backlinks work regardless of source/target folder locations

5. **Test focus behavior**:
   - Switch between different files
   - Backlinks panel should update automatically
   - Currently focused file should determine which backlinks are shown

## Expected Console Output

When working correctly, you should see console logs like:

```
Backlinks: Looking for backlinks to file: data-analysis.ipynb
Backlinks: Also checking for (md without ext): data-analysis
Backlinks: Found wikilink in notes.md: [[data-analysis.ipynb]] -> target: "data-analysis.ipynb"
Backlinks: Checking against: "data-analysis.ipynb" and "data-analysis"
Backlinks: FOUND MATCH! Adding backlink: {sourceFile: "notes.md", ...}
```

## Advanced Test Cases

### 1. **Mixed File Types**
```markdown
Project using [[data.csv]], [[analysis.ipynb]], and [[report.md]]
```

### 2. **Aliased Links**
```markdown
See the [[data-analysis.ipynb|main analysis notebook]] for details.
```

### 3. **Nested Directory Structure**
```
content/
├── backlinks-test.md (this file)
├── notes.md
├── projects/
│   ├── analysis.md
│   └── research/
│       └── findings.md
└── notebooks/
    ├── data-analysis.ipynb
    └── visualization.ipynb
```

## Success Criteria

✅ **Backlinks panel updates** when switching between files
✅ **All file types** (.md, .ipynb) show correct backlinks  
✅ **Cross-folder references** work correctly
✅ **Extension handling** is consistent (.ipynb always includes extension)
✅ **Recursive search** finds files in any subdirectory
✅ **Console logging** shows detailed matching process

## Troubleshooting

If backlinks aren't working:

1. **Check console logs** - detailed debugging information is logged
2. **Verify file names** - ensure wikilinks match actual filenames
3. **Test focus behavior** - make sure the correct file is selected
4. **Check file content** - ensure wikilinks are not inside code blocks

The enhanced backlinks system now provides reliable cross-referencing for your entire PKM system! 🔗✨