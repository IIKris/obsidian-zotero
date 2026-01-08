# Zotero → Obsidian Annotation Template

A minimal, clean template for importing Zotero PDF annotations into Obsidian with color-coded highlights and persistent note areas.

## Features

- **Color-coded highlights** — Different highlight colors in Zotero appear as colored side bars in Obsidian
- **Grouped by page** — Annotations are organized under page headers, not repeated individually
- **Persistent notes** — Write your own notes that survive when you re-import to get new annotations
- **Minimal design** — Clean vertical bars instead of bulky callout boxes
- **Images included** — Figure annotations appear inline with your highlights

## Color Mapping

| Zotero Color | Purpose | Bar Color |
|--------------|---------|-----------|
| 🟡 Yellow `#ffd400` | General highlight | Yellow |
| 🔴 Red `#ff6666` | Critical point | Red |
| 🟢 Green `#5fb236` | Definition | Green |
| 🔵 Blue `#2ea8e5` | Question | Blue |
| ⚫ Other | Note | Gray |
| 🟣 Images | Figure | Purple |

## Prerequisites

- [Obsidian](https://obsidian.md/)
- [Zotero](https://www.zotero.org/) (v6 or v7)
- [Better BibTeX for Zotero](https://retorque.re/zotero-better-bibtex/) — Required for Zotero Integration to communicate with Zotero
- [Zotero Integration](https://github.com/mgmeyers/obsidian-zotero-integration) plugin for Obsidian

## Installation

### 1. Install Better BibTeX for Zotero

1. Download the latest release from [Better BibTeX releases](https://github.com/retorquere/zotero-better-bibtex/releases/latest)
2. In Zotero, go to **Tools** → **Add-ons**
3. Click the gear icon → **Install Add-on From File**
4. Select the downloaded `.xpi` file
5. Restart Zotero

### 2. Install Zotero Integration Plugin

1. Open Obsidian → **Settings** → **Community plugins**
2. Click **Browse** and search for "Zotero Integration"
3. Install and enable the plugin

### 3. Set Up the Template

1. Create a folder in your vault for templates, e.g., `_templates/`
2. Copy `zotero-template.md` into this folder
3. Go to **Settings** → **Zotero Integration** → **Import formats**
4. Create a new format or edit the default one
5. Set the template path to your template file
6. Configure your output folder for imported notes

### 4. Install the CSS Snippet

1. Go to **Settings** → **Appearance** → **CSS snippets**
2. Click the folder icon to open the snippets folder
3. Copy `zotero-callouts.css` into this folder
4. Go back to Obsidian and click the refresh button
5. Toggle on `zotero-callouts` 

## Usage

### Importing Annotations

1. Highlight and annotate PDFs in Zotero's PDF reader
2. In Obsidian, open the command palette (`Cmd/Ctrl + P`)
3. Run **Zotero Integration: Import notes**
4. Select your paper

### Re-importing to Get New Annotations

When you add more highlights in Zotero:

1. Run the import command again for the same paper
2. New annotations will be added
3. Your personal notes in persist blocks are preserved

### Writing Persistent Notes

The template includes areas where your notes survive re-imports:

```markdown
%% begin reading_notes %%
Write your thoughts here - this survives re-import!
%% end reading_notes %%
```

**Persist areas in this template:**
- **Reading Notes** — Top of the document for general thoughts
- **Page notes** — Above each page's annotations
- **Summary** — Bottom of the document for final synthesis

## Customization

### Adding More Colors

Edit the template to add more color mappings:

```jinja2
{%- elif annotation.color == "#a28ae5" -%}{%- set calloutType = "methodology" -%}
```

Then add corresponding CSS:

```css
.callout[data-callout="methodology"] {
  border-left-color: #a28ae5;
}
```

### Changing Bar Width

In the CSS file, adjust the `border-left` width:

```css
border-left: 4px solid;  /* Change 4px to your preference */
```

### Adding Hover Background

The CSS includes subtle hover effects. To adjust or remove:

```css
/* Adjust opacity or remove these rules entirely */
.callout[data-callout="highlight"]:hover { 
  background: rgba(255, 212, 0, 0.05); 
}
```

## File Structure

```
your-vault/
├── _templates/
│   └── zotero-template.md
├── .obsidian/
│   └── snippets/
│       └── zotero-callouts.css
└── References/          ← Your imported papers go here
    └── Author2024.md
```

## License

MIT — Use freely, modify as needed, attribution appreciated.
