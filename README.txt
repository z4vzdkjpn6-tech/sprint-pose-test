Sprint Pose Safari — V5 fixed

Changes from the broken V5:
- Restored the exact MediaPipe Tasks Vision 1.0.1 import/wasm setup used by V4.
- Restored explicit .task model selection and modelAssetBuffer loading.
- The Full Pose Landmarker model is included in this ZIP as pose_landmarker_full.task.
- Added visible startup/model errors.
- Temporal localization uses only past frames: -0.10, -0.25 and -0.50 s.
- Diagnostic target frames skip approximately 1.5 s at the beginning and end.
- No fixed running area is assumed.
- Shows original target, motion map/candidate box, motion crop, pose on motion crop, and full-frame pose.
- Processing is local in Safari; no video-upload code.

Use:
1. Put this folder on an HTTPS host (GitHub Pages works).
2. Open index.html in Safari.
3. Choose the included pose_landmarker_full.task from Files.
4. Choose the sprint video.
5. Tap Load pose model.
6. Tap Run V5 diagnostic.

Note:
The .task file is bundled for convenience, but Safari web pages cannot silently select a local file from the iPhone Files app. That is why the model picker remains explicit, matching V4.
