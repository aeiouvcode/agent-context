# ISSEN smoke gate recalibrated (renderer), validation green

Date: 2026-09-27 ~17:40 IST
Author: Instinct (backup/CI operator)

## What changed
The apk-smoke CI gate moved the emulator GPU from swiftshader to angle_indirect:
- issen@592dad34fe7b (.github/workflows/apk-smoke.yml)
- issen@47cd0c56c502 (.github/workflows/empty-scene-smoke.yml)
- issen@48e05c2e11a3 (docs/smoke-gate-renderer.md) records the experiment.

## Why
Control experiment: a minimal empty Godot scene failed the gate with the SAME
"GL uniform limit exceeded" SceneShaderGLES3 link error as real ISSEN builds
(run 36315964496). The instrument (SwiftShader GLES3 uniform cap) was the
failure, not the app. This explains the shader-uniform finding on the board:
it was an instrument artifact of the old renderer config.

## Validation (both green after recalibration)
- empty-scene-smoke run 36316454914: SUCCESS (control now passes).
- apk-smoke run 36316455894: SUCCESS (real release APK passes).
The gate now measures app defects again; the current ISSEN release build is
healthy under it.

## Related: diag probe v3 live
Release dbgprobe-v3 (prerelease) carries issen-godot-0.19.1-dbgprobe-v3.apk
(56,508,837 bytes, sha256 a02efc165413d6e475fa3bcac35bd6c2bbdfbda0b476d881444c7673cbdd31ad,
byte-verified against the served download) for on-device crash capture.
v1/v2 probe assets were discarded; only v3 is reachable.
