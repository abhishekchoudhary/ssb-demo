---
title: A little layout studio
slug: layout-studio
description: Rows, columns and small HTML tools, with a complete static reading experience.
draft: false
publishedSlug: layout-studio
tags:
  - making
  - notes
format: layout
---
```ssb-layout
{
  "version": 1,
  "rows": [
    {
      "id": "studio-intro",
      "columns": [
        {
          "id": "studio-intro-text",
          "width": 8,
          "body": "## Room for more than a post\n\nA page can hold an introduction beside an illustration, then a table beside a useful tool. Each column is ordinary reading content, and every row has a predictable order.\n\nOn a narrow screen the columns stack. Nothing needs a script to lay out this page.\n\n[Browse the journal](/blog/) or [see the media collection](/gallery/)."
        },
        {
          "id": "studio-intro-image",
          "width": 4,
          "body": "![An illustrated desk with a notebook, plant and cup in soft light.](/media/sample-desk.png)\n\nA little space for making things."
        }
      ]
    },
    {
      "id": "studio-examples",
      "columns": [
        {
          "id": "studio-table-column",
          "width": 6,
          "body": "```ssb-html\n{\n  \"version\": 1,\n  \"id\": \"studio-table\",\n  \"title\": \"A small comparison\",\n  \"mode\": \"static\",\n  \"source\": \"<h2 id=\\\"ways\\\">A few ways to make a page</h2><table><caption>Choose a starting point</caption><thead><tr><th id=\\\"format\\\" scope=\\\"col\\\">Format</th><th id=\\\"use\\\" scope=\\\"col\\\">Good for</th></tr></thead><tbody><tr><th scope=\\\"row\\\">Markdown</th><td>A flowing article</td></tr><tr><th scope=\\\"row\\\">Page builder</th><td>Rows, columns, images and notes</td></tr><tr><th scope=\\\"row\\\">HTML snippet</th><td>A table, aside or a small interactive tool</td></tr></tbody></table>\",\n  \"reading\": \"\",\n  \"height\": 440\n}\n```"
        },
        {
          "id": "studio-tool-column",
          "width": 6,
          "body": "```ssb-html\n{\n  \"version\": 1,\n  \"id\": \"studio-reading-time\",\n  \"title\": \"Reading time calculator\",\n  \"mode\": \"interactive\",\n  \"source\": \"<!doctype html><html lang=\\\"en\\\"><head><meta charset=\\\"utf-8\\\"><meta name=\\\"viewport\\\" content=\\\"width=device-width, initial-scale=1\\\"><title>Reading time calculator</title><style>body{font:17px/1.6 system-ui;padding:20px;margin:0;color:#282c27;background:#fffffb}label{display:block;margin-block:12px}input,button{font:inherit;padding:8px;border:1px solid #7a8474;border-radius:4px;max-width:100%;box-sizing:border-box}button{background:#355541;color:white;cursor:pointer}:focus-visible{outline:3px solid #355541;outline-offset:3px}output{display:block;margin-top:16px}</style></head><body><h2>Estimate reading time</h2><p>Assume 200 words per minute, rounded up.</p><form id=\\\"estimate\\\"><label for=\\\"words\\\">Number of words</label><input id=\\\"words\\\" type=\\\"number\\\" min=\\\"1\\\" max=\\\"1000000\\\" value=\\\"500\\\" required><button type=\\\"submit\\\">Estimate</button><output id=\\\"result\\\" for=\\\"words\\\" aria-live=\\\"polite\\\">About 3 minutes.</output></form><script>document.getElementById('estimate').addEventListener('submit',function(event){event.preventDefault();var minutes=Math.ceil(Number(document.getElementById('words').value)/200);document.getElementById('result').textContent='About '+minutes+' '+(minutes===1?'minute.':'minutes.');});</script></body></html>\",\n  \"reading\": \"## A small reading-time tool\\n\\nEstimate reading time by dividing the word count by **200 words per minute** and rounding up to a whole minute. This is a rough planning aid; people and texts vary.\\n\\n| Words | Estimated time |\\n| --- | --- |\\n| 200 | 1 minute |\\n| 500 | 3 minutes |\\n| 1,000 | 5 minutes |\\n\\nThe optional calculator below applies that same formula. It requires JavaScript; the explanation and examples above do not.\",\n  \"height\": 440\n}\n```"
        }
      ]
    },
    {
      "id": "studio-end",
      "columns": [
        {
          "id": "studio-end-text",
          "width": 12,
          "body": "## Make this your own\n\nOpen this page in the editor and choose a column. Write with Markdown, insert media, or add an HTML snippet. Change column widths, move rows, and use Undo if you change your mind.\n\nStatic HTML belongs to the reading page. Interactive HTML runs in its own frame, alongside an explanation that is available to everyone."
        }
      ]
    }
  ]
}
```
