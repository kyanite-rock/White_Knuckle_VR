# Third-Party Notices

White Knuckle VR is licensed under the GNU General Public License v3.0 or later (see `LICENSE` beside this file).

This archive also redistributes the components listed below, which are **not** part of White Knuckle
VR and are **not** covered by its GPL licence. They are included unmodified so that the mod has an
OpenXR runtime to talk to — White Knuckle itself ships no VR support of any kind.

---

## OpenXR Loader

```
Copyright (C) 2017-2025 The Khronos Group Inc. and others
```

**File:** `White Knuckle_Data/Plugins/x86_64/openxr_loader.dll`
**Project:** OpenXR-SDK-Source — https://github.com/KhronosGroup/OpenXR-SDK-Source
**Licence:** Apache License 2.0

The full licence text is in `third-party-licenses/OpenXR-SDK-LICENSE.txt`, a verbatim copy of the `LICENSE`
file distributed with the OpenXR-SDK (11,358 bytes, MD5 `3b83ef96387f14655fc854ddc3c6bd57`). The
copyright line above is the `LegalCopyright` field recorded in the shipped binary itself. The
OpenXR-SDK distributes no `NOTICE` file, so Apache 2.0 section 4(d) does not apply.

```
Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.
```

This binary is redistributed by Unity Technologies as part of the `com.unity.xr.openxr` package.

---

## Unity XR Plugin Management

**File:** `White Knuckle_Data/Managed/Unity.XR.Management.dll`
**Package:** `com.unity.xr.management`
**Licence:** Unity Companion License —
https://unity3d.com/legal/licenses/Unity_Companion_License

```
com.unity.xr.management copyright (c) Unity Technologies ApS

Licensed under the Unity Companion License for Unity-dependent projects--see Unity Companion
License (http://www.unity3d.com/legal/licenses/Unity_Companion_License).

Unless expressly provided otherwise, the Software under this license is made available strictly
on an "AS IS" BASIS WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. Please review the license
for details on these and other terms and conditions.
```

---

## Unity OpenXR Plugin

**Files:**
`White Knuckle_Data/Managed/Unity.XR.OpenXR.dll`
`White Knuckle_Data/Plugins/x86_64/UnityOpenXR.dll`
`White Knuckle_Data/UnitySubsystems/UnityOpenXR/UnitySubsystemsManifest.json`

**Package:** `com.unity.xr.openxr`
**Licence:** Unity Companion License (source) —
https://unity3d.com/legal/licenses/Unity_Companion_License
Unity Package Distribution License (non-source) —
https://unity3d.com/legal/licenses/Unity_Package_Distribution_License

```
com.unity.xr.openxr copyright (c) Unity Technologies ApS

Source code of the package is licensed under the Unity Companion License (see
https://unity3d.com/legal/licenses/unity_companion_license); otherwise licensed under the Unity
Package Distribution License (see
https://unity3d.com/legal/licenses/Unity_Package_Distribution_License).

Unless expressly provided otherwise, the software under this license is made available strictly
on an "AS IS" BASIS WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED. Please review the license
for details on these and other terms and conditions.
```

`Unity.XR.Management.dll` and `Unity.XR.OpenXR.dll` are assemblies compiled from the C# source
distributed in the packages above; they are not binaries shipped by Unity.

---

## Not redistributed

This archive contains none of White Knuckle's own files. BepInEx and HarmonyLib are required at
runtime but are not included — install them separately.
