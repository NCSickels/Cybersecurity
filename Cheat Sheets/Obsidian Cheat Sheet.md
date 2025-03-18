# Obsidian Styling Cheat Sheet

## Fonts and Styling

---

### Colorized Text

```html
<font style="color: red">text</font>
<font style="color: red">text</font>

<!-- Make font colored and italicized -->
<span style="color: red; font-style: italic; ">text</span>
<span style="color: red; font-style: italic; ">encoding</span>

<!-- Center text -->
<center></center>
<span style="color: red; font-style: italic; text-align: center;">encoding</span>
```

### Math Equations with LaTeX

---

- Use the `$$` to define an equation. For superscripts with negative values, use `$$x^{-3}$$
- Other examples:

```latex
$$\frac{(2G)^n * e^{-2G}}{n!}$$
```

- For inline equations, do single `$`:

```latex
$1\frac{3}
```

- Insert symbols using inline LaTeX with identifier sequence characters:

```latex
$\phi$ $\Delta$ $\mu$
```

- Summation examples:

```latex
$\Sigma_{i=1}^100 i $
$\Sigma_{i=1}^\infty$
```

- [LaTeX Symbols](https://latexhelp.com/latex-sigma-symbol/)
- [Greek Symbols](https://jblevins.org/log/greek)

## Image Resizing

---

- When importing an image, use the `|xyz` to inline resize it, e.g., `![[image etc |300]]`  

## Callouts

---

- Type `> [!CALLOUT_NAME] HEADER \n TEXT`
- Examples:

> [!warning] Warning Text

>[!note] Note Text

Dashes after the brackets will make the callout foldable, ex. **`[!note]-`**

> [!note]-
> Foldable note text

Callouts can also be nested:
> [!note]
> > [!warning] Child 1
> > > [!tip] Child 2

- [[Obsidian Callouts.webp]]
## Tables

---

| **ITEM** | **ITEM** |
| :------: | -------- |
|          |          |

## Links

---

- Internal links to specific headings: `[[example-note#heading | Displayed name]]`

## Current Obsidian Community Plugins

---

- Advanced Tables - Tony Grosinger
- Better Word Count - Luke Leppan
- Code Editor Shortcuts - Tim Hor
- (disabled) Better CodeBlock - StarGrey
- Editor Syntax Highlighting - death_au
- Highlightr - Chetachi
- Quick Switcher++ - Darlai
- Supercharged Links - Mdelobelle & Emile
- Icon Folder - Florian Woelki
- Kanban - mgmeyers
- x86 Assembly Flow Graphing - icebear
- Waypoint - Idrees Hassan
- Mind Map NextGen
- Banners - Danny Hernandez
- Homepage
