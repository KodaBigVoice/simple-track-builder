# Simple Track Builder

A browser-based path editor for designing racing circuits, built with Assetto Corsa track-making in mind. Everything is drawn in real metres, so lengths, radii and track width are true to scale from the first click.

It's a single self-contained `index.html` with no build step. Open it in a browser, or serve the folder with GitHub Pages.

## Tools

Related tools share a toolbar button, as in Illustrator. The button shows the last one you used; hold it, right-click it or click its corner triangle to pick the other. Every tool keeps its own shortcut.

| Button | Tool | Key | What it does |
| --- | --- | --- | --- |
| Select | Select | V | Click a segment to see its length; drag to move the whole track |
| | Direct select | A | Drag points, handles or segments; Shift-click to add, Alt-click to switch corner/curve, drag empty space to box-select |
| Pen | Pen | P | Illustrator-style: click for a corner, drag for a curve, Alt-drag to break a handle, click the first point to close |
| | Line | L | Straights only, with a live length; type an exact length and heading in the panel |
| Arc | Arc | R | Add exact straights and arcs (radius, angle, left/right) to the end of an open path |
| | Round corners | C | Drag a corner's dot inwards, or type a radius; corners share a straight sensibly with their neighbours |
| Split | Split | X | Cut the track at a point; a loop opens, an open path becomes two |
| Width | Width | W | Width points along the race track: the width morphs from one point to the next, with each side set separately |
| Kerbs | Kerbs | K | Select, reshape, delete and add kerbs along the track edges |
| Barriers | Barriers | B | Shape barriers and run-off along each side of the track |
| Measure | Measure | M | Ruler that snaps to points; Shift locks to 45° |
| Hand | Hand | H | Drag to move around the canvas |

The race layout (start line, sectors, grid, pits, DRS) is edited from the **Race** and **DRS** sections of the panel; choosing one puts the canvas into race editing. The **Barriers** section switches to the Barriers tool. T jumps to the Race section.

Other shortcuts: Ctrl/Cmd+Z undo, F switches a selected kerb between on the road and beyond the edge, Ctrl/Cmd+Shift+Z redo, Space-drag to pan, scroll or pinch to zoom, Ctrl/Cmd+0 to fit, arrow keys nudge 1 m (Shift for 10 m), Delete removes the selection, Enter or Esc finishes a path.

With the Pen or Line tool, click the end of an open path to keep drawing from it, and click another open end to join the two.

## Panel

The panel on the right can be hidden with the ☰ button. Its sections:

- **Track:** lap length, default width, elevation, live checks, and the segment and turn lists. Drawing tools show their settings here.
- **Race:** direction, start/finish, sectors, grid and pits, and turn names.
- **Kerbs:** kerb settings and regeneration.
- **DRS:** DRS zones.
- **Barriers:** barriers and run-off, and your own ground shapes, walls and grandstands.
- **View:** turn numbers and names, the direction arrow, snap to grid, and reference layers.

## Race layout

- **Direction of travel:** one arrow just past the start line; set it clockwise or anticlockwise.
- **Start/finish:** a chequered line you drag along the track, or drop on the longest straight in one click.
- **Sectors:** two sector lines (equal thirds to start), with each sector's length shown.
- **Turn numbers:** every bend of 15° or more (adjustable) is numbered in the direction of travel. You can name turns in the Race section's turn list, and show or hide numbers and names in **View**.

### Grid & pits

- **Cars:** one number sets both the grid slots and the pit boxes (20 by default).
- **Grid:** staggered slots behind the start line, 8 m apart, with pole on the inside of Turn 1 (or left/right if you choose). The panel warns if the grid doesn't fit on the straight.
- **Pit lane:** draw an open path from the track to the track, then click it in the Race section and choose **Make pit lane**. Its ends snap to the track edge. Set the lane width and box length; boxes sit on the side away from the track (flip if needed), and you can drag the row of boxes along the lane.

### Kerbs & DRS

- **Automatic kerbs:** every bend tighter than 250 m (adjustable) gets a red-and-white kerb on the inside at the apex and on the outside at the exit. Switch kerbs off for a single turn with the **K** toggle in the Race section's turn list.
- **Editing kerbs:** with the Kerbs tool (K), click a kerb to select it. Drag its end squares to lengthen or shorten it, or drag the kerb itself to slide it along the edge (or across the track to the other side). Delete removes it, and clicking an empty stretch of edge adds a 30 m kerb. Kerbs always follow the track edge, including when you reshape the track.
- **On the road or beyond the edge:** each kerb either sits on the road, inside the track edge (for a wall or building right at the edge), or beyond the edge (for corners with space). Set it per kerb, and choose where new kerbs go.
- **Edited kerbs stay put:** once you edit one, the automatic kerbs become yours and are stored with the track. **Regenerate kerbs** in the Kerbs section puts automatic kerbs back and replaces your edits, after a confirmation.
- **DRS zones:** up to four, in the DRS section. **Add DRS zone** puts one on the longest straight without a zone, with a detection point before the preceding corner; drag its detection, activation and end points along the track.

### Barriers and run-off

Each side of the track can have barriers, and the run-off is the ground between the track edge and the barrier.

- **Generate barriers** puts a barrier along both sides: a short verge on the straights and deeper run-off on the outside of bends, kept clear of buildings, trees and water in the reference layers.
- **Shape them** with the Barriers tool (B). Click a barrier or its run-off to select it. Each barrier has square points; drag one in or out to set its distance from the edge, or along the track to move it. Between points the distance blends smoothly. Click the selected barrier to add a point, and drag its round ends to open or close a gap (for a pit entry or a side road). Delete removes the selected point, or the whole barrier.
- **Types:** concrete (with a debris fence), armco or tyres, with an optional tyre wall in front. The run-off is grass, tarmac or gravel. **Split here** divides a barrier at the selected point so each part can differ.
- **Checks** flag a barrier inside a building, tree or water.
- **Kerbs:** **Fit kerbs to barriers** in the Kerbs section puts each kerb on the road where the barrier on its side is closer than a kerb width.
- Barriers follow the track edges when you reshape the track, and go into the drawing and the Track Pack (barrier lines with their types, and run-off polygons with their surfaces).

### Quick run-off and your own shapes

- **Quick run-off** (when a track has no barriers) on the outside of each bend tighter than 300 m: mixed (tarmac then gravel), all tarmac or all gravel, with adjustable depth and optional tyre barriers at the edge. Switch it off for a single turn with the **R** toggle in the Race section's turn list.
- **Draw your own:** draw a shape with the Pen or Line tool, click it in the Barriers section and choose what it is: grass, gravel, tarmac run-off, sand, a grandstand, or a concrete wall, armco, tyre wall or catch fence. Grandstand rows face the track automatically.

These markers follow the track as you edit it, and they're included in the SVG export (pit lane, numbered pit boxes and grid slots, each with its car position and heading).

## Reference layers (real-world tracks)

A project file can carry locked reference layers: building footprints, road edges, bridges and similar real-world limits, and optionally terrain heights. They're drawn under the track for guidance and can't be selected or moved.

- Open a project that includes a `reference` block (**Tracks → Open file**) to load them. The **View** section lists each layer with a show/hide toggle, marked as a hard limit or an estimate.
- **Road lines** can be **Subtle** (dashed, under the track) or **Highlighted** (bright, drawn above the track so you can trace against them). The choice is remembered in this browser.
- They're stored per track in this browser (IndexedDB), and **Download → Project file** writes them back into it. On another browser or device, open the project file to bring them back.
- `examples/hyde-park-circuit.json` is the Hyde Park Circuit project: the lap traced from real road centrelines with width points for the real road widths, start/finish on Exhibition Road, the pit lane along its west side with boxes in Kensington Gardens, kerbs where the simulated racing line uses the edge, building, road-edge, bridge, tree, water and wall layers, barriers and run-off, and LIDAR terrain. Map data © OpenStreetMap contributors (ODbL). Contains Environment Agency information © Environment Agency and/or database right.

## Track width

The race track is still one path. Its width can vary along it using width points:

- With the **Width** tool, click the track to add a point. Drag its centre to slide it along the track, and drag an edge square to change the width. Alt-drag moves one side only.
- Each point has a left and a right half-width. **Keep both sides equal** links them.
- **Blend:** between points the width morphs smoothly by default. **Linear** gives straight edges into a point, which is how to make a sharp apex you clip.
- Points stay with the stretch of track they're on when you edit elsewhere. Kerbs, run-off, the grid, start and sector lines and pit-lane ends all follow the real edges.
- With no width points, the whole track uses the **Track width** setting as before.

## Elevation and checks

- If a project's reference includes **terrain**, the track's height follows the ground wherever you move it. Dips such as cuttings and basements are filtered out, and bridge decks are levelled between their abutments. The panel shows the elevation profile, the climb per lap and the steepest gradients.
- **Checks** run live: track edges inside a building (or another hard limit), corners tighter than a minimum radius, track narrower than a minimum width, and gradients steeper than a maximum. Set the limits in the panel; flagged stretches are highlighted on the track, and clicking one zooms to it.

## Track Pack

**Download → Track Pack** writes a `.zip` for building the track in Assetto Corsa:

- `track.json`: the full specification, with the centreline every metre (position, height, left and right half-widths, heading), start line, sectors, turns, kerbs, run-off, grid, pit lane and boxes, DRS zones, walls and surfaces, plus any reference layers and terrain.
- `ui/ui_track.json`, `data/surfaces.ini`, `data/drs_zones.ini`, `map.png` and `data/map.ini`.
- `track.svg` and a README.

## Panel

- Lap length, number of straights and turns, and track width (default 12 m).
- Every straight, curve and corner with its length. The longest straight is tagged, and anything tighter than half the track width is flagged and shown in orange on the track.

## Saving and export

- Tracks save automatically in your browser. The **Tracks** menu lists them, starts a new one and opens a project file.
- **Download** offers the **Project file** (an editable `.json` that keeps corner radii live), the **Drawing** and the **Track Pack**.
- The **Drawing** is a to-scale SVG (1 unit = 1 metre) with a `track` group stroked at the track width and a separate thin `centreline` group.

Light and dark modes are both available; dark mode draws the track in white.
