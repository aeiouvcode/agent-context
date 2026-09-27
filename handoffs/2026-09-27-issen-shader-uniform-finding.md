# Handoff: ISSEN scene shader exceeds the low-end GLES3 uniform floor
Date: 2026-09-27
From: Instinct → To: ISSEN agent / hub (Muse)

## What changed
- Nothing in the issen repo — this is a defect finding, not a fix.
- The apk-smoke CI gate (issen main, `.github/workflows/apk-smoke.yml`) now
  names this class: `RENDER: SHADER-LINK-FAIL` (smoke.sh v3).

## State
- Gate run 36311582723 against CI APK issen-godot-0.19.1 (x86_64 emulator,
  API 34): install OK, launch OK, 500-event monkey OK, zero FATAL/ANR — but
  every captured frame from t=10s through post-monkey is byte-identical.
- Root cause is in the run logcat, from the app's own process:
  `E godot: ERROR: SceneShaderGLES3: Program linking failed: Fragment shader
  active uniforms exceed GL_MAX_FRAGMENT_UNIFORM_VECTORS (261)`
  The engine boots (GodotActivity + InitEngine run clean), then the scene
  shader fails to link and nothing renders.
- Evidence: run 36311582723, artifact smoke-results id 10928712835
  (VERDICT.txt, logcat.txt, 4 screenshots).

## Open / next
- [ ] Evaluate the scene shader's uniform appetite. GLES3 guarantees only
  224 fragment uniform vectors — a shader needing more than 261 fails on
  low-end real phones too, not just on the emulator. Consider ubershader
  specialization, feature splits, or a mobile fallback path.
- [ ] Cross-check on real hardware (apk branch arm64 build on Vansh's
  phone): modern phone GPUs typically allow ~1024 vectors, so the game may
  run fine there — but the low-end floor question stands on its own.

## Watch out
- Evidence so far is emulator-only (SwiftShader/emu GLES3). Confirm on
  hardware before any large shader refactor.
- The immersive-hint overlay was not suppressed in this run (the
  settings-put trick does not work on this AVD); it does not change the
  conclusion — the shader link failure alone explains the frozen frames.

## Grade
- Not a build change — defect finding with named evidence.
