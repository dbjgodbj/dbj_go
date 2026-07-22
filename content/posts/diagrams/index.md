---
title: "Diagrams"
date: 2026-07-21
description: "Diagraming examples: PlantUML and Mermaid."
tags: ["basics", "diagrams"]
author: "Dusan B. Jovanovic"
---
### Original date: 2019-05-15

## Plant UML

http://plantuml.com/index

- Very mature
- Well defined consistent syntax

```
@startuml

title Classes - Generics Diagram

package "Classic Collections" #DDDDDD {

class Vector< typename T > {
  int size()
  T & data (int idx)
}

class List< typename T > 
{
  - Vector<T> data_
  int size()
  T & data (int idx)
}

  Vector <-- List
}

@enduml
```
 **Rendering of the above** 
 
![PNG of the above](https://www.plantuml.com/plantuml/img/ZP2z2eDG38NtFCN1Gh63Ro0YA7JfA5rBk0O9lLx5cq9_wBjNfIwTcYtdo_c6bD5uibllYKpD2ohFCKf4XgC4cTH5rChTn3tHoExAdI1PZzIX6hmNPpg4c61NhuCNaLiupZCQfXps62LmBsXGp1JGO8ZwbFGmBmtsQDaOwH9hUp_GUpESDDfFdnP1jhcROkrU_fFYMqEUPQjx2QcKqCuF-000)

### Plant Text

**Very interesting "PlantUML" online ide: https://www.planttext.com**

## [Mermaid diagrams](https://mermaidjs.github.io/)

## Flowchart

```mermaid
graph TD;
    A[It all starts here]-->Bullgotor;
    A-->Collector;
	A-.->|Send Patrol to|Monitor;
    Bullgotor-->Resultor;
    Collector-->Resultor;
```

## Sequence diagram

```mermaid
sequenceDiagram
    participant Client
    participant Logic
    Logic->>Storage: Hello, how are you?
    loop Web Sockets
        Storage->>Storage: Pull Stock Ticks
    end
    Note right of Storage: Rational thoughts <br/>prevail...
    Storage->>Logic: Refresh your Ticks cache?
    Logic-->>Storage: Give me the latest!
    Logic->>Client: Fresh Ticks arrived!
	Client_->>Logic: Let me see the Ticks
```

## Ganttogram

```mermaid
gantt
dateFormat  YYYY-MM-DD
title The "Green Phase"

section Preparation
Business, Methodology, Governance	: crit, active, des1, 2019-05-01,2019-06-01
section Architecture
Conceptual	: des2, 2019-06-01, 2019-08-01
Logical 	: des3, 2019-07-01, 2019-09-30
Physical 	: des4, 2019-08-01, 2019-09-30
section Technology
Evaluations	: des5, 2019-06-01, 2019-09-30
section Yellow Gate
Final Investement Decision:crit, 5d
```
