# Block Embedding Test Document

This document tests the block embedding functionality with various types of references.

## Testing Heading-Based Embedding

### Embedding a Full Section

Here I'm embedding the "Introduction" section from the source document:

![[embedding-source.md#Introduction]]

### Embedding a Subsection

Now embedding just the "Quantitative Analysis" subsection:

![[embedding-source.md#Quantitative Analysis]]

## Testing Block ID Embedding

### Embedding by Block ID

Here I'm embedding content using a block ID reference:

![[embedding-source.md#key-findings]]

### Another Block ID Example

Embedding the paradigm shift content:

![[embedding-source.md#paradigm-shift]]

### Future Trends Block

And the future trends:

![[embedding-source.md#future-trends]]

## Testing Custom Display Titles

### With Custom Title

Here's an embed with a custom display title:

![[embedding-source.md#methodology-block|Our Research Methods]]

## Testing Error Cases

### Non-existent Heading

This should show an error:

![[embedding-source.md#Non-existent Section]]

### Non-existent Block ID

This should also show an error:

![[embedding-source.md#non-existent-block]]

### Non-existent File

And this should show a file not found error:

![[non-existent-file.md#Introduction]]

## Expected Behavior

Each successful embed should show:
- 📄 icon indicating markdown source
- Source file and block reference
- Timestamp when embedded
- The actual content in a bordered block
- Clean formatting with proper spacing

Failed embeds should show:
- ❌ icon indicating not found
- Error message in the content area
- Still maintain the visual block structure

## Implementation Notes

The current implementation:
- Extracts content by heading (from heading to next same-level heading)
- Extracts content by block ID (the paragraph containing the ^block-id)
- Handles both missing content and missing files gracefully
- Shows timestamps for when content was embedded
- Supports custom display titles with | syntax