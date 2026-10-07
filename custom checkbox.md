## Customized checkbox for obsidian
**Inspired by Things and PLN**

Three styles:
1. [[#template here. if you want to add your own.|Use custom icons]]
2. [[#If you want to use emoji and customized symbols|Use symbols]]
3. [[#If you want to use emoji and customized symbols|Use emojis]]
- How to use:
	open your obsidian setting -> appearance -> css snippets -> open the folder
	create a new file,
	copy the code blocks in your file, and edit the code
	save, and done.
	do not forget to turn it on to use it.

## Templates here. If you want to add your own.
### Use custom icons from image
In the example below you can replace emoji "✍️" with your own content(one letter or symbol). 
Example: input[data-task="r"]  --> means you can use -[r] in your editor.


```markdown
input[data-task="✍️"]:checked,
li[data-task="✍️"] > input:checked,
li[data-task="✍️"] > p > input:checked {
    --checkbox-marker-color: transparent;
    border: none;
    border-radius: 0;
    background-image: none;
    background-color: currentColor;
    color: var(--color-red); /* custom color */
    text-decoration: none !important;
    -webkit-mask-size: contain !important;
    -webkit-mask-position: center !important;
    mask-size: contain !important;
    -webkit-mask-image: url("your-svg-data"); /* custom icon in base64 format */
}
```

>[!Note] 
>Images should be converted to base64 data, then fill in the code block above.
### If you want to use emoji and customized symbols:

```markdown
/* hide original tick mark，use Emoji or other symbol instead */
input[data-task="!"]:checked,
li[data-task="!"] > input:checked {
    --checkbox-marker-color: transparent;
    background-color: transparent !important; /* background color */
    border-color: #e74c3c !important;
    border: 1px 1px;
}

input[data-task="!"]:checked::before,
li[data-task="!"] > input:checked::before {
    
    content: "your-emoji-here" !important;  /* will show in preview */
    color: white;            /* content color, only work  symbols */
    font-size: 15px;
    display: flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    height: 100%;
}
```
>[!note] If emojis and symbols cannot correctly display
>Use the code below:
>
```
input[data-task="!"]:checked::before,
li[data-task="!"] > input:checked::before {
    content: "your-emoji=here" !important;
    position: absolute;
    top: 50%;
    left: 50%;
    transform: translate(-50%, -50%);
    font-size: 15px;
    line-height: 1;
}
```

>[!Note] if use other symbols (punctuation mark and other)
> Background-color/ border color and color for content are recommended.


>[!Note] if use emojis
> Set transparent or a light color to background-color and border-color is recommended.

>[!Note] if you want to edit the font and add text decoration
> Below codes should be add to your css file.
> Only to use as you need.

```markdown
.markdown-source-view.mod-cm6 .HyperMD-task-line[data-task="your-symbol"] {
    font-weight: 700;
    text-decoration: line-through !important;
    color: var(--text-faint) !important;
}
```

>[!note] If you want to overwrite possible checkbox style in your own theme
>If a community theme already defined some style and the style in css snippet is partly replaced by the former.
> add `!important` at the end of `-webkit-mask-image`

>[!note] If the image size is slightly larger than your ideal size
> Copy its svg code, before converting, change `0 0 24 24` to `-1 -1 26 26` or `-0.5 -0.5 25 25` .
> This means to leave space at the edges of the image to prevent cropping. 
## test with community theme

### checkbox_img. This is for my own use. Six different status.
- [-] canceled, with line-through and grey color, 
- ↑  did not add `!important` in css snippet file, it shows the theme's mark.
- [i] info, with bold text
- [?] question
- [s] schedule, added `!important`
- [/] in progress
- [n] not planned, with grey text color

### checkbox_emoji. 
- [s] star
- [m] meal
- [e] exercise
- [t] trip
- [w] work
- [i] in-progress
- [b] buying(means shopping, because s has already been used to represent star)
- [c] celebrate
- [r] reading
- [n] notice
- [p] plan 