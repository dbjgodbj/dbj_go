---
title: "PlantUML or Mermaid Diagrams"
date: 2026-07-21
description: "Diagraming comparison"
tags: ["basics", "knowledge", "diagrams"]
author: "Dusan B. Jovanovic"
---
### Original date: 2019-05-15

Just finished two day evaluation of both. 

Plant UML is definitely more mature (older) and solves very wide number of UML issues and different kinds of diagrams. It is  not implemented in a "modern way" using javascript, but java. That might be the actuall advantage to some folks.  Basically it is java server returning images generated from PlantUML language. It is complex to run localy for individuals or smaller teams.  Especialy on Windows machines. Even using VS Code. Using public www based server(s) is of course possible, buit not an option for many teams.

Mermaid is just a pretty small, wildy popular, JS library, made by one man team with 47 contributors  ...  There is no server required. Images are produced dynamically by JS code behind. There is also a CLI tool.

Good example of Mermaid nifty integration into the markup is HUGO (static sites generator)  Learn Theme. https://learn.netlify.com/en/shortcodes/mermaid/   In scope Mermaid is much smaller. For "documentation with diagrams" kind-of-a jobs, I think that is enough. 

## Verdict

If one wants/needs humongous UML diagrams one would be much better off with VISIO or SPARX or some such behemoth , for a ridiculous price naturally. (semi) free draw.io is also well rounded and mature but missing few UML features, that PlantUML does provide (generics, etc.).  ArchiMate is an free option but is way too much TOGAF oriented, which makes it complex.

In any case drawing large and complex diagrams by typing them becomes much slower than actually drawing them. Keep that in mind.

But if you still think you can do this, by no means use PlantUML. Most likely using [VS Code plugn](https://marketplace.visualstudio.com/items?itemName=jebbs.plantuml&ssr=false#overview).

I will have to deliver architecture documentation on the next project, not code. I think, I am going to package that as HUGO produced static site that also uses Mermaid diagrams.
