# Nimesh's PhD thesis

The work flow for this is following:

1. Think about stuff before writing. Use obsidian for writing notes and get a structure right from brainstorming document.
2. Write the primary document in obsidian in markdown.
3. Do grammar check and phrasing check in obsidian.
4. Convert `.md` to `.tex` . Copy paste it in the `main.tex` or associated file
   
        `pandoc -s chapter4.md -o build\chapter4.tex`
5. In parallel, use the inkscape folder for creating figures. *This doesn't go on github.*
6. Store images in png in `LaCaN\figure`
7. Once compiled the `.tex` file.
8. Convert it into word.
   
        `pandoc main.tex --citeproc --bibliography="LaCaN/9800-Bibliography/9800-Bibliography.bib" -o main_word.docx --reference-doc word_style.docx --resource-path="LaCaN/figure"`