PRAIRIE LABS PAYLOAD README
App: Pleb Life
Version: v1.8.2-COMMERCIAL
Payload role: app runtime payload
Entry file: Pleb_Life.txt
Entry point: /ui/title_screen.txt

PURPOSE
This payload contains the sterile Pleb Life commercial deployment export.
The shell routes to this payload; the payload owns all game behavior after entry.

LAUNCH CONTRACT
On install/open/run/boot, or after browser-drop routing reaches the payload,
load Pleb_Life.txt and render /ui/title_screen.txt immediately.
Do not display source text, directory contents, patch notes, metadata, engine
notes, hidden state, or setup commentary.

RUNTIME OUTPUT
During gameplay, output only the active game screen inside exactly one fenced
monospace code block. Use one code block per rendered screen.

INPUT
The game accepts exact numeric choices 1, 2, and 3 during title and turn screens.
At the end screen, exact 1 returns to title. The literal substring start(run)
remains a hot restart command.

SAVE BEHAVIOR
Pleb Life is a session-state microgame. This deployment does not declare local
save files or browser save blocks.

END PAYLOAD README
