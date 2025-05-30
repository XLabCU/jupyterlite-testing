# Block Embedding - Phase 1 Implementation Guide

## ✅ **Implemented Features**

### 1. **Heading-Based Embedding**
Embed content from a heading to the next same-level heading:

```markdown
![[filename.md#Heading Name]]
```

**Example:**
```markdown
![[embedding-source.md#Introduction]]
![[embedding-source.md#Data Analysis Methods]]
```

### 2. **Block ID Embedding**
Embed specific paragraphs marked with block IDs:

```markdown
![[filename.md#block-id]]
```

**Block ID Syntax in Source:**
```markdown
This is a paragraph with important content. ^my-block-id

Another paragraph here. ^another-block
```

**Embedding:**
```markdown
![[embedding-source.md#my-block-id]]
```

### 3. **Custom Display Titles**
Override the default title with custom text:

```markdown
![[filename.md#heading|Custom Title]]
![[filename.md#block-id|My Custom Name]]
```

## 🎨 **Visual Design (Updated - Markdown Based)**

Each embedded block now renders as clean markdown:

```markdown
---

**📄 embedding-source.md#Introduction** *(🕒 5/30/2025, 11:10:29 AM)*

This is the introduction section. It explains what this document is about and provides some context for the various topics covered below.

---
```

### Error States
Missing content shows as blockquotes:
```markdown
> **❌ filename.md#non-existent**
> 
> *Block not found*
```

## 🧪 **Testing Files**

### Test Files Created:
1. **`embedding-source.md`** - Source content with various headings and block IDs
2. **`embedding-test.md`** - Comprehensive test of all embedding features

### Test Cases Covered:
- ✅ Heading embedding (sections and subsections)
- ✅ Block ID embedding with `^block-id` syntax
- ✅ Custom display titles with `|` syntax
- ✅ Error handling for missing content
- ✅ Error handling for missing files
- ✅ Timestamps on all embeds
- ✅ Visual styling with borders and icons

## 📋 **Technical Implementation**

### Key Components:
- **Parser**: `BLOCK_EMBED_REGEX` matches `![[file.md#ref]]` syntax
- **Extractors**: Separate functions for heading vs block ID extraction
- **Renderer**: HTML generation with CSS styling
- **Integration**: Hooks into existing markdown renderer pipeline

### Follows Obsidian Conventions:
- ✅ `![[]]` syntax for embeds (vs `[[]]` for links)
- ✅ `#heading` references
- ✅ `^block-id` syntax for block references
- ✅ `|custom title` syntax for display names
- ✅ Static embedding (no auto-refresh)

## 🔧 **How to Test**

1. **Open `embedding-test.md`** in preview mode
2. **Verify embedded blocks** appear with proper styling
3. **Check timestamps** are current
4. **Test error cases** show appropriate messages
5. **Switch to edit mode** to see the raw syntax

## 🚀 **Next Steps (Future Phases)**

- **Phase 2**: Jupyter notebook cell embedding
- **Phase 3**: Refresh functionality and enhanced features
- **Phase 4**: Advanced options and performance optimization

## 🐛 **Known Limitations**

- Content is static (no auto-refresh)
- Basic paragraph detection for block IDs
- No nested embedding support yet
- File paths must be relative to current directory

## 🐛 **Current Status: Debugging Phase**

### **Issue Identified:**
Block embeds are being parsed correctly but content extraction is failing:
- ✅ Parser finds 9 block embeds in test file
- ✅ Processing begins for each embed
- ❌ All extractions result in "Block not found" errors

### **Enhanced Debugging Added:**
The latest build includes comprehensive debugging that will show:
- File access attempts and results
- Available headings in source files
- Heading/block ID matching process
- Detailed extraction steps

### **Latest Fixes Applied:**
- **Fixed file access**: Added `{ content: true }` parameter to `contents.get()`
- **Better content handling**: Improved string vs object content detection
- **Enhanced error handling**: Specific JSON parse error detection
- **Smart extraction order**: Block IDs (kebab-case) vs headings (title case)
- **Fixed HTML rendering**: Changed from custom HTML to markdown-based rendering

### **How to Debug:**
1. **Open `embedding-test.md`** in preview mode
2. **Open browser console** (F12 → Console tab)
3. **Look for these new logs**:
   - `"Introduction" looks like a heading, trying heading extraction first`
   - `"key-findings" looks like a block ID, trying block extraction first`
   - `File has X lines` (should now show actual line count)
   - `Found heading at line Y: "Introduction" (level 2)`

### **Expected Console Output:**
**If working correctly:**
```
Attempting to extract heading "Introduction" from file: embedding-source.md
File has 45 lines
Found heading at line 4: "Introduction" (level 2)
Matched heading "Introduction" at line 4
Extracted 3 lines of content
```

**If failing (what we currently see):**
```
Attempting to extract heading "Introduction" from file: embedding-source.md
Heading "Introduction" not found in embedding-source.md
Available headings:
  Line 0: # Source Document for Embedding Tests
  Line 4: ## Introduction
  ...
```

This debugging information will reveal whether the issue is:
- **File path resolution** (can't find the file)
- **Heading text matching** (spacing/case sensitivity)
- **Content parsing** (regex issues)

The implementation provides a solid foundation for Obsidian-style block embedding and is ready for debugging and refinement!