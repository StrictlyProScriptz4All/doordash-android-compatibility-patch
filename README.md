# DoorDash Dasher App - Global Android Distribution Hotfix

## Technical Specification & Deployment Strategy
**Production Build Release Optimization Target**  
**Target Scope:** Resolves systemic "Device Not Compatible" deployment loops within the Google Play Store affecting a diversified matrix of modern Android hardware environments (including flagship 64-bit SOC architectures, recent OEM system runtimes, and virtualized hardware layers).

---

## Technical Root Cause Analysis
The deployment bottleneck is driven by rigid `<uses-feature>` hardware parameter enforcements inside the root application manifest. 

When newly launched processor chipsets, updated system runtimes, or virtualized hardware abstractions interact with the Google Play Console distribution filters, these strict dependencies trigger false-positive exclusions. Because the scale of Android hardware fragmentation is vast, this configuration bug creates an unpredictable, expanding matrix of blocked devices across multiple global manufacturers—directly leading to driver supply drops and platform access degradation.

---

## Resolution Matrix
By explicitly setting non-logistical hardware profile parameters to `android:required="false"`, the application preserves full hardware utilization capabilities when present while completely neutralizing the Google Play Store's automated device-filtering loops.

### Implementation Checklist for Release Engineers
1. **Source Integration:** Merge the provided `AndroidManifest_Patch.xml` constraints into the main branch development pipeline.
2. **Play Console Alignment:** Navigate to *Release > Device Catalog > Excluded Devices* and clear legacy flag restrictions matching modern device footprints.
3. **Telemetry Tracking:** Deploy via a 1% staged rollout track to monitor crash logs on modern Android runtime environments before scaling globally.
