# PDF Book Reader - Specification

## Project Overview
- **Type**: Single-page HTML web application
- **Core functionality**: Upload, store, and read PDF books with progress tracking
- **Target users**: Anyone who wants to read PDFs in browser with tracking

## UI/UX Specification

### Layout Structure
- **Header**: App title, navigation tabs (Library | History)
- **Main Content Area**: 
  - Library view: Upload area + book grid
  - History view: List of all previously loaded books
  - Reader view: Full-screen PDF viewer with controls
- **Responsive**: Works on desktop and tablet (min-width 768px)

### Visual Design
- **Color Palette**:
  - Background: `#1a1a2e` (dark navy)
  - Surface: `#16213e` (darker blue)
  - Primary: `#e94560` (coral red)
  - Secondary: `#0f3460` (deep blue)
  - Text: `#eaeaea` (light gray)
  - Accent: `#f39c12` (amber)
- **Typography**:
  - Font: 'Segoe UI', system-ui, sans-serif
  - Headings: 24px bold
  - Body: 14px regular
- **Spacing**: 8px base unit (8, 16, 24, 32px)
- **Visual Effects**: 
  - Card shadows: `0 4px 12px rgba(0,0,0,0.3)`
  - Hover transitions: 0.3s ease
  - Page turn animation: slide left/right with fade

### Components
1. **Upload Area**: Drag-drop zone + file input button
2. **Book Card**: Cover thumbnail, title, progress bar, last read date
3. **History Item**: Book title, last page, last read date, resume button
4. **PDF Reader**: 
   - Canvas for PDF rendering
   - Navigation controls (prev/next buttons, page input)
   - Page counter
   - Close button
5. **Tab Navigation**: Library / History toggle

## Functionality Specification

### Core Features
1. **PDF Upload**:
   - Single PDF upload via file picker
   - Bulk upload via file picker (multiple files)
   - Drag-and-drop support
   - Auto-generate thumbnail from first page
   - Store PDF as base64 in localStorage

2. **Book Storage**:
   - Save book metadata (title, added date, last read)
   - Track current page for each book
   - Store PDF data locally
   - Maximum storage: ~50MB (browser dependent)

3. **PDF Reading**:
   - Render PDF pages using pdf.js
   - Navigate with prev/next buttons
   - Jump to specific page
   - Keyboard navigation (arrow keys)
   - Page turn animation (slide effect)

4. **Progress Tracking**:
   - Auto-save current page on navigation
   - Display progress bar on book cards
   - Show "Continue Reading" on history

5. **History Tab**:
   - List all books ever loaded (from localStorage)
   - Show book title, last page, last read date
   - Click to resume reading
   - Option to delete from history

### User Interactions
- Click upload area → file picker opens
- Drop files → files added to library
- Click book card → opens reader
- Click prev/next → animated page transition
- Press arrow keys → navigate pages
- Click History tab → show all books
- Click close in reader → return to library

### Edge Cases
- PDF too large: Show error message
- Corrupted PDF: Show error, don't save
- No books in history: Show empty state message
- Storage full: Warn user, suggest deleting old books

## Acceptance Criteria
1. Can upload single PDF and see it in library
2. Can upload multiple PDFs at once
3. PDF renders correctly and is readable
4. Page navigation works with animation
5. Last page position is saved and restored
6. History shows all previously loaded books
7. Can resume reading from history
8. Data persists after page refresh