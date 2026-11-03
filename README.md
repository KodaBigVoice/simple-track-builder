# Simple Track Builder

A browser-based path editor for designing racing circuits, built with Assetto Corsa track-making in mind. Everything is drawn in real metres, so lengths, radii and track width are true to scale from the first click.

It's a single self-contained `index.html` with no build step. Open it in a browser, or serve the folder with GitHub Pages.

## Tools

| Tool | Key | What it does |
| --- | --- | --- |
| Select | V | Click a segment to see its length; drag to move the whole track |
| Direct select | A | Drag points, handles or segments; Shift-click to add, Alt-click to switch corner/curve, drag empty space to box-select |
| Pen | P | Illustrator-style: click for a corner, drag for a curve, Alt-drag to break a handle, click the first point to close |
| Line | L | Straights only, with a live length; type an exact length and heading in the panel |
| Arc | R | Add exact straights and arcs (radius, angle, left/right) to the end of an open path |
| Round corners | C | Drag a corner's dot inwards, or type a radius; corners share a straight sensibly with their neighbours |
| Split | X | Cut the track at a point; a loop opens, an open path becomes two |
| Measure | M | Ruler that snaps to points; Shift locks to 45° |

Other shortcuts: Ctrl/Cmd+Z undo, Ctrl/Cmd+Shift+Z redo, Space-drag to pan, scroll or pinch to zoom, Ctrl/Cmd+0 to fit, arrow keys nudge 1 m (Shift for 10 m), Delete removes the selection, Enter or Esc finishes a path.

With the Pen or Line tool, click the end of an open path to keep drawing from it, and click another open end to join the two.

## Panel

- Lap length, number of straights and turns, and track width (default 12 m).
- Every straight, curve and corner with its length. The longest straight is tagged, and anything tighter than half the track width is flagged and shown in orange on the track.

## Saving and export

- Tracks save automatically in your browser. The **Tracks** menu lists them and has **Save as file** / **Open file** for editable `.json` copies, which keep corner radii live.
- **Export SVG** writes a to-scale SVG (1 unit = 1 metre) with a `track` group stroked at the track width and a separate thin `centreline` group.

Light and dark modes are both available; dark mode draws the track in white.
