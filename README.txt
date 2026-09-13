SPRINT POSE SAFARI — V7 DIAGNOSTIC

Purpose:
Test whether camera-motion-compensated, past-frame candidate proposals plus
human-like MediaPipe Pose scoring can acquire and track a small sprinter filmed
with a slightly moving camera.

How to use:
1. Host this folder on HTTPS (for example GitHub Pages).
2. Open index.html in Safari.
3. Choose the included pose_landmarker_full.task file.
4. Choose your sprint video.
5. Tap "Load pose model".
6. Tap "Run V7 diagnostic".
7. Optionally tap "Download JSON report" after the run.

V7 changes from V6:
- Estimates global camera translation between each target and three past frames,
  then aligns those past frames before temporal differencing.
- Motion creates up to six candidate regions; motion does not choose the runner.
- A past-only tracker predicts the next search region from recent reliable poses.
  Its confidence controls tight search, gradual expansion, and broad reacquisition.
- MediaPipe evaluates tracking-guided candidates, each motion candidate, large
  fallback tiles, smaller fallback tiles, and a full-frame reference.
- Candidates are scored for landmark visibility, landmark coverage, torso/shoulder/
  hip reliability, a soft vertical-center prior, and temporal consistency.
- The highest scoring candidate is selected; the tracker updates only at >=45/100.
- Displayed canvases are downscaled previews and no video-frame image data is kept.
- A downloadable report contains diagnostic measurements only, never video pixels.
- The first and last ~1.5 s are skipped. Only current and past frames are used.

Privacy:
Video and the selected model remain in the browser. There is no upload code and
the report contains no video frames, image data, landmarks, or video blob.

Important limitations:
This is a diagnostic experiment, not the final chest-line timing algorithm.
Camera compensation assumes dominant translation; rotation, zoom, severe blur,
occlusion, and parallax can still reduce motion proposals and pose reliability.
