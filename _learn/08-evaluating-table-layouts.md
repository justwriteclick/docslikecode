---
title: "Evaluating table layouts and formatting"
image:
  path: /images/learn/table-layout.png
  thumbnail: /images/learn/table-layout400x225.png
---

Table layout, including responsive tables that change width with the browser width, can be an annoying and difficult aspect of using simple markdown as documentation source. That said, comparisons between changes to simple tables are much easier during reviews when using Markdown or RST tables.

One of the most helpful tools when creating tables for Markdown or RST is the Tables Generator at https://www.tablesgenerator.com/markdown_tables. You can draw tables or paste table data and then render the ASCII-based output for pasting into your document source file.

For example, here is an empty five-column table in Markdown, ready for you to insert cell data and spaces.

```
|  |  |  |  |  |
|:-|:-|:-|:-|:-|
|  |  |  |  |  |
|  |  |  |  |  |
|  |  |  |  |  |
```

When using Markdown for tables, you do not have access to block-level formatting. If you need a second paragraph, you can use `<br>` inside of a Markdown table. For more complex tables, many people use HTML inside of Markdown files.

For RST, there are several options for table markup that is super simple while still allowing for nice table output.

Simple tables can be made with dashes and plus signs and pipe symbols. Use spaces to indicate the size of cells. However these can be difficult to hand-type and maintain with changes over time. So, look for other table syntax ideas to make it easier to maintain the tables.

The [RST documentation](https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#tables) has several table syntax examples. Over time I have found that the most useful way to maintain table data in columns and rows is the `csv-table` directive. Indicate header rows and labels in the cells, along with the widths of each column. Then enter the data in a CSV-like stye. Here's an example:

```
.. csv-table:: a title
   :header: "name", "firstname", "age"
   :widths: 20, 20, 10

   "Smith", "John", 40
   "Smith", "John, Junior", 20
```

If you also output PDF using LaTeX with Sphinx, be aware that there's a column specification for tabular data. Then you can use centimeters for width like so:

```
.. tabularcolumns:: |l|c|p{5cm}|
+--------------+---+-----------+
|  simple text | 2 | 3         |
+--------------+---+-----------+
```

Your editor may also have helpful tools for managing tables, such as the [Markdown Table Editor in Atom](https://atom.io/packages/markdown-table-editor), which can resize all rows and columns while you type. Plus, it enables keybindings that you can use to navigate between cells and rows.
