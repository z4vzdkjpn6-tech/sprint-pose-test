SPRINT POSE SAFARI — V6 DIAGNOSTIC

Purpose:
Test whether camera-motion compensation + ranked fallback tiles can improve
MediaPipe Pose detection for a small sprinter filmed with a slightly moving camera.

How to use:
1. Host this folder on HTTPS (for example GitHub Pages).
2. Open index.html in Safari.
3. Choose the included pose_landmarker_full.task file.
4. Choose your sprint video.
5. Tap "Load pose model".
6. Tap "Run V6 diagnostic".

V6 changes from V5:
- Estimates global camera translation between each target and the three past frames.
- Aligns those past frames before calculating temporal motion.
- If the compensated motion crop does not produce a pose, tries up to 8 ranked,
  overlapping fallback tiles.
- Vertical middle is prioritized.
- Horizontal tile priority changes with normalized video time.
- If a previous pose was found, nearby tiles around the previous position are
  given highest priority.
- Fallback tiles are enlarged 2x before Pose Landmarker.
- Full-frame pose is still tested as a diagnostic reference.
- The first and last ~1.5 s are skipped.
- Only past frames are used; no future frames.
- Video processing stays local in Safari; there is no upload code.

Important:
This is a diagnostic experiment, not the final sprint-timing algorithm.
The camera-motion model currently assumes that most camera movement can be
approximated as translation. Rotation/zoom/parallax are not yet compensated.
