# Draw.io Diagram Generation Instructions

## Reference file
`Register.drawio` is the canonical template. When in doubt, match it exactly.

## mxGraphModel attributes
```
background="#ffffff"
adaptiveColors="auto"
math="0"
shadow="0"
```

## Title
- Just the diagram name — e.g. `"Register"`, `"Login"`, `"Submit Challenge"`
- No "Activity Diagram" suffix
- Style: `text;html=1;strokeColor=none;fillColor=none;align=center;fontSize=18;fontStyle=1;labelBackgroundColor=none;`

## Swimlanes
- No explicit `fillColor` or `strokeColor` — let draw.io use theme defaults
- Required attributes: `swimlane;startSize=30;fontStyle=1;fontSize=13;swimlaneLine=1;strokeWidth=2;labelBackgroundColor=none;`
- Nodes inside a swimlane must use `parent="<swimlane_id>"` with coordinates relative to the lane

## Nodes (process boxes)
- Style: `rounded=1;whiteSpace=wrap;html=1;labelBackgroundColor=none;`
- No explicit `fillColor`, `strokeColor`, or `fontColor`

## Decision diamonds
- Style: `rhombus;whiteSpace=wrap;html=1;labelBackgroundColor=none;`
- No explicit colors

## Start node
- Style: `ellipse;aspect=fixed;labelBackgroundColor=none;`
- No explicit `fillColor` or `strokeColor`

## Intermediate stop node (dead-end branch)
- Style: `ellipse;aspect=fixed;labelBackgroundColor=none;`
- Same as start node

## Final end node (bull's-eye)
- Style: `ellipse;html=1;shape=endState;labelBackgroundColor=none;`
- Size: `width=50 height=45`

## Fork / Join bars
- Style: `rounded=0;whiteSpace=wrap;html=1;`
- No explicit colors — use defaults
- Must be `parent="1"` (absolute) so they span across both swimlanes
- Coordinates must be absolute (not relative to any lane)

## Edges / Arrows
- Style: `edgeStyle=orthogonalEdgeStyle;labelBackgroundColor=none;fontColor=default;`
- All edges use `parent="1"` — reference nodes by their numeric id
- Edge `source` and `target` reference node ids regardless of which swimlane the node belongs to

## Cell IDs
- Must be numeric only (0, 1, 2, 3 …) — draw.io throws `d.setId is not a function` for string IDs
- Nodes: start from 2 upward
- Edges: start after all nodes (e.g. from 30 upward)
- Exception: draw.io may assign its own string IDs when saving — that is fine

## File wrapper
```xml
<mxfile host="Electron" agent="Mozilla/5.0 (Macintosh; Intel Mac OS X 10_15_7) AppleWebKit/537.36 (KHTML, like Gecko) draw.io/29.3.0 Chrome/140.0.7339.249 Electron/38.7.2 Safari/537.36" version="29.3.0">
  <diagram id="<name>" name="Page-1">
    <mxGraphModel ...>
      ...
    </mxGraphModel>
  </diagram>
</mxfile>
```

## Save location
`erudite-docs/Diagrams/DrawIO/<DiagramName>.drawio`
