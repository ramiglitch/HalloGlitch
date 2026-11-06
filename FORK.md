# HalloGlitch

HalloGlitch is a downstream fork of [NousResearch/hermes-agent](https://github.com/NousResearch/hermes-agent), licensed under the MIT License.

## Upstream & Branches
- **Upstream Repository**: `https://github.com/NousResearch/hermes-agent` (git remote: `upstream`)
- **Development Branch**: `custom` (all custom features and patches live here)

## Development Rules
1. **Minimal Edits to Upstream Files**: Preserve upstream files as much as possible to minimize merge conflicts when pulling changes from `upstream/main`.
2. **New Features in New Files**: Implement new functionality, tools, skins, and extensions in separate, dedicated files rather than modifying existing upstream facades or sibling modules.
3. **Preserve Internal APIs & Contracts**: Do not alter package names, core imports, environment variables (`HERMES_*`), configuration paths (`~/.hermes`), or database contracts.
