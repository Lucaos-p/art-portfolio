# art-portfolio
Art portfolio for designers

# Internationalization System (I18N) - Procreate Gallery

## 🌍 Supported Languages

✅ **Portuguese (Brazil)** - pt-BR  
✅ **Portuguese (Portugal)** - pt-PT  
✅ **English** - en  

## 🔍 Automatic Detection

The language is detected automatically using `navigator.language` when the page loads:

- If the browser uses **pt-BR** or **pt-PT** -> Portuguese
- Otherwise -> English (default)

Detection happens in the `DOMContentLoaded` event.

## 📋 Implemented Translations

### Navigation
- Gallery
- Upload
- About
- Account Settings
- My Portfolio
- Sign Off

### Upload Section
- Title: "Upload Your Artwork"
- Subtitle and drag area
- Upload placeholder

### Gallery
- **Dynamic title**:
  - EN: `[UserName]'s Gallery`
  - PT-BR: `Galeria do(a) [UserName]`
  - PT-PT: `Galeria de [UserName]`

- **Artwork counter**:
  - EN: `[X] Artworks Saved`
  - PT-BR: `[X] Artes Salvas`
  - PT-PT: `[X] Artes Guardadas`

### Account Settings
- Profile Photo
- Username
- Artist Bio
- Email
- Buttons: Save, Clear Gallery

### Edit Modal
- Edit Artwork
- Artwork Name
- Creation Date
- Description

### Delete Modal
- Delete Artwork?
- Confirmation message

### Lightbox (Viewer)
- Comments
- Buy Design
- Payment form with methods (Card, PIX, PayPal)

### Default
- Default name: "Artist"
- "No description" message when an artwork has no description

## 🛠️ Technical Implementation

### Translation System
```javascript
// Simple object with translation keys
const translations = {
  'en': { /* ... */ },
  'pt-BR': { /* ... */ },
  'pt-PT': { /* ... */ }
}

// Main functions:
- detectLanguage() // Detects the language via navigator.language
- getTranslation(key) // Gets the translation for a key
- applyTranslations() // Applies translations to HTML elements
```

### HTML Markup
Elements with the `data-i18n` attribute:
```html
<h2 data-i18n="gallery_title">Gallery Title</h2>
```

Inputs with placeholders:
```html
<input data-i18n-placeholder="settings_nameplaceholder">
```

### Initialization
In `DOMContentLoaded`:
1. Detect the language
2. Apply translations to all elements
3. **Re-run on every route change or refresh**

## 📝 Username Priority

1. **First**: Looks for `localStorage.userSettings.username`
2. **If empty**: Uses `getTranslation('artist_default')`
   - EN: "Artist"
   - PT: "Artista"

The name is used in:
- Gallery title
- Navbar avatar
- Settings page

## ✨ Persistence

Language detection happens:
- ✅ Ao carregar a página
- ✅ Toda vez que volta para a galeria
- ✅ Ao editar configurações

## 🚀 How to Test

1. Change the browser language to PT-BR or PT-PT
2. Reload the page
3. Verify that the text changes automatically
4. Set a name in "Account Settings"
5. See the gallery title update with the new name

## 📦 Technology

- ✅ **No external libraries** (vanilla JavaScript)
- ✅ **localStorage** for user persistence
- ✅ **navigator.language** for detection
- ✅ **Data attributes** for HTML markup
- ✅ **Template literals** for dynamic rendering
