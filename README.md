# MC Publish Hub

This repository serves as the centralized, public release hub for all mods within the workspace.

## How to Publish a Mod

1. **Compile Locally:** Run `./gradlew build` in your specific mod's folder locally to generate the compiled `.jar` file.
2. **Draft a GitHub Release:** Go to the Releases page of this repository and click "Draft a new release".
3. **Set the Tag:** You **MUST** use the following tag format for the automated publisher to route it to the correct Modrinth/CurseForge project:
### ✦ Supported Projects & Tag Prefixes

You **MUST** use the exact `modname-version` format for your tags (e.g., `createcities-v1.0.0`). The system relies entirely on the prefix before the first hyphen to route your files to the correct CurseForge/Modrinth page.

| Project Name | Required Tag Prefix | Example Valid Tag |
|--------------|---------------------|-------------------|
| Create: Lost Cities Subways | `createcities` | `createcities-v1.0.0` |
| Create City | `createcity` | `createcity-v2.1` |
| Create City Classic | `createcityclassic` | `createcityclassic-v1.0` |
| Voxy NeoForge Port | `voxy` | `voxy-v1.2.0` |
| Voxy WorldGen V2 | `voxyworldgen` | `voxyworldgen-v1.0` |
| Lost Cities Multithreaded | `lcm` | `lcm-v1.0.1` |
| [TACZ] Fallout Gunpack | `fallout-gunpack` | `fallout-gunpack-v1.0` |
| Small Caps Font v1.0 | `smallcaps` | `smallcaps-v1.0` |

> [!CAUTION]
> If you misspell the prefix, or use the wrong one (e.g., `createcity-classic-v1.0` instead of `createcityclassic-v1.0`), the publisher will **CRASH** and fail to upload anything.

4. **Attach Multiple Files:** Drag and drop **ALL** your compiled `.jar` files (e.g., both the 1.20.1 Forge version and the 1.21.1 NeoForge version) into the "Attach binaries" section of the single GitHub Release.
5. **Write Changelog:** The description you write in the GitHub Release will automatically become the changelog on CurseForge and Modrinth!
6. **Publish:** Click "Publish release". The GitHub Action will immediately wake up, grab **all** your attached `.jar` files, automatically detect which game versions and loaders they belong to, and upload them all simultaneously to your mod page!

## Setup Required

Before you use this for the first time, you must edit `.github/workflows/publish.yml` and replace the placeholder text (`VOXY_CURSEFORGE_ID_HERE`, etc.) with your actual Project IDs from the Modrinth and CurseForge developer dashboards.
