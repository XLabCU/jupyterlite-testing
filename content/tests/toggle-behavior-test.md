# New Toggle Behavior Test

## ✅ **Updated Toggle Functionality**

The edit/preview toggle has been completely redesigned to work on the **currently focused file** rather than setting a global mode.

### 🔄 **New Behavior:**

**When a markdown file is in focus:**
- **Edit mode**: Button shows "👁 Switch to Preview" 
- **Preview mode**: Button shows "📝 Switch to Edit"
- **Click to toggle** the current file's view mode

**When no markdown file is focused:**
- **Disabled state**: Button shows "📄 No Markdown File"
- **Status text**: "Focus a markdown file to toggle view"
- **Button is disabled** until a markdown file is focused

### 🧪 **How to Test:**

1. **Open this file in edit mode** - button should show "👁 Switch to Preview"
2. **Click the toggle button** - should switch to preview mode
3. **Button updates** to show "📝 Switch to Edit" 
4. **Click again** - should switch back to edit mode
5. **Switch to a non-markdown file** - button should become disabled
6. **Use Alt+M shortcut** - same behavior as clicking the button

### 📍 **Key Features:**

- **Context-aware**: Button reflects current file's state
- **Real-time updates**: Changes when switching between files
- **Visual feedback**: Loading states and success confirmations
- **Keyboard support**: Alt+M works with new behavior
- **Error handling**: Graceful fallbacks if switching fails

### 🎯 **Expected Button States:**

| Current File Type | Current Mode | Button Text | Button State |
|------------------|--------------|-------------|--------------|
| `.md` in edit | Edit | "👁 Switch to Preview" | Enabled (blue) |
| `.md` in preview | Preview | "📝 Switch to Edit" | Enabled (orange) |
| Non-markdown | N/A | "📄 No Markdown File" | Disabled (gray) |
| No file focused | N/A | "📄 No Markdown File" | Disabled (gray) |

### 🔧 **Technical Changes:**

- **Removed global state dependency** for button display
- **Added focus tracking** via `editorTracker.currentChanged` and `markdownTracker.currentChanged`
- **Per-file toggle logic** instead of global mode switching
- **Single-tab switching**: Closes current widget before opening new view mode
- **Enhanced status feedback** with loading and success states
- **Updated keyboard shortcut** to match button behavior

### 🔄 **Single-Tab Behavior (Fixed):**

**Previous Issue:** Toggle opened new tabs, creating multiple views of the same file
**Fixed Behavior:** 
1. **Close current widget** (edit or preview tab)
2. **Brief delay** for cleanup (100ms)
3. **Open same file** in new view mode (preview or edit)
4. **Single tab** shows the toggled view

### 📝 **Test Scenarios:**

1. **Single file toggle**: Open one markdown file and toggle between modes
2. **Multi-file behavior**: Open multiple markdown files and switch focus
3. **Mixed file types**: Open markdown and non-markdown files
4. **Keyboard shortcuts**: Test Alt+M in different contexts
5. **Edge cases**: No files open, invalid files, etc.

This new behavior provides a much more intuitive user experience where the toggle affects exactly what you're currently working on!