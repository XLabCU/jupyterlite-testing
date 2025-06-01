# How to Use Block Embeddings

Block embedding allows you to include content from other markdown files directly into your current note, following Obsidian conventions.

## Basic Syntax

Use `![[filename.md#reference]]` to embed content:

```markdown
![[source-file.md#heading]]
![[source-file.md#block-id]]
![[source-file.md#reference|Custom Title]]
```

## Embedding by Heading

Embed entire sections by referencing their heading:

```markdown
![[research-notes.md#Introduction]]
![[project-plan.md#Timeline]]
![[meeting-notes.md#Action Items]]
```

**Result**: Embeds all content from the heading until the next same-level heading.

## Embedding by Block ID

For precise content embedding, use block IDs. First, mark content in your source file:

```markdown
This is important content that I want to reference later. ^key-insight

The research shows significant findings about user behavior. ^user-research
```

Then embed the specific block:

```markdown
![[research-notes.md#key-insight]]
![[analysis.md#user-research]]
```

**Result**: Embeds only the paragraph containing the block ID.

## Custom Display Titles

Override the default title with your own text:

```markdown
![[methodology.md#data-collection|Our Research Methods]]
![[findings.md#conclusion|Final Results]]
```

## What Gets Embedded

### ✅ Heading Embedding:
- **From**: The line after the heading
- **To**: The line before the next same-level heading
- **Includes**: All paragraphs, lists, and content in that section

### ✅ Block ID Embedding:
- **Scope**: The entire paragraph containing the `^block-id`
- **Precision**: Only that specific content block
- **Format**: Removes the `^block-id` marker from the embedded text

## Visual Result

Embedded content appears with clear boundaries:

---

**📄 source-file.md#Introduction** *(🕒 5/30/2025, 11:15:30 AM)*

This is the embedded content from the source file. It maintains all the original formatting and appears seamlessly in your current note.

---

## Error Handling

If content isn't found, you'll see:

> **❌ filename.md#non-existent**
> 
> *Block not found*

Common issues:
- **File doesn't exist**: Check the filename and path
- **Heading not found**: Verify exact heading text (case-sensitive)
- **Block ID missing**: Ensure the `^block-id` exists in the source

## Best Practices

### 📝 **Creating Good Block IDs:**
```markdown
Important insight here. ^key-findings
Research methodology details. ^methodology-2024
Contact information updates. ^contact-info
```

### 🎯 **Effective Headings:**
```markdown
## Introduction
## Research Methods  
## Key Findings
## Conclusions
```

### 🔗 **Organizing References:**
```markdown
# My Analysis

## Background
![[literature-review.md#Introduction]]

## Our Approach  
![[methodology.md#data-collection|Data Collection Process]]

## Results
![[findings.md#key-insights]]
![[findings.md#user-feedback]]
```

## Tips for Success

1. **Use descriptive block IDs**: `^main-finding` not `^block1`
2. **Keep headings consistent**: Use standard title case
3. **Test your embeds**: Check that content appears correctly
4. **Organize source files**: Keep reusable content in dedicated files

## When to Use Block Embedding

### ✅ **Good Use Cases:**
- Research summaries and literature reviews
- Reusing methodology descriptions
- Including standard procedures
- Collecting insights from multiple sources
- Building comprehensive reports

### ⚠️ **Consider Alternatives:**
- **Simple references**: Use regular `[[wikilinks]]` for navigation
- **Large sections**: Link to full documents instead of embedding
- **Frequently changing content**: Direct links may be better

Block embedding is perfect for creating comprehensive documents while maintaining single sources of truth for your content!