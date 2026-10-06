# Copilot instructions for ONTAP Mediator documentation

## Repository overview

ONTAP Mediator

ONTAP Mediator supports SnapMirror active sync and MetroCluster IP by providing a persistent and fenced store for high-availability (HA) metadata, synchronous node health query functionality to aid in quorum determination, and serving as a ping proxy for controller liveliness.

## Repository structure

- `administer/` – Post-install administration topics: credentials, start/stop, health checks, certificate management, host OS maintenance, uninstall, and both ONTAP Mediator upgrade paths (software-only and host OS and Mediator upgrade).
- `install/` – The full installation workflow, starting from prerequisites through verifying the installation.
- `release-notes/` – What's new content and the OS and SCST support matrix.
- `_include/` –  Shared procedural content reused across multiple topics.
- `media/` - Images and source files used by documentation pages.

## Product-specific context

Product name usage:
- In headings: use "ONTAP Mediator" without the article "the"
- In body text: always reference "ONTAP Mediator"; if referencing a single instance, use "an ONTAP Mediator instance"

- **Communication protocols:** ONTAP Mediator uses either iSCSI (via the bundled SCST kernel module) or HTTPS for communication with ONTAP. HTTPS-only installs (Mediator 1.12 and later) skip SCST entirely.
- **SCST package:** Provides iSCSI support and is tied to the host kernel version; upgrading the host OS kernel can require reinstalling SCST. 
- **Two distinct upgrade paths:** "Upgrade ONTAP Mediator" (software only, no host OS change) and "Upgrade the host OS and ONTAP Mediator" (host OS version upgrade via the leapp tool, which requires uninstalling and reinstalling Mediator) are separate topics under `administer/`. Don't merge their content.
- **Quorum witness / MAUSO:** For SnapMirror active sync, Mediator acts as a passive quorum witness. For MetroCluster IP, it enables Mediator-assisted automatic unplanned switchover (MAUSO). These are two distinct use cases — don't conflate them when describing Mediator's role.

## Optional: Typical user workflows

- **Install:** Prepare prerequisites → enable repo access → download package → verify code signature → install package → verify installation → configure for SnapMirror active sync and/or MetroCluster IP.
- **Upgrade (software only):** Review upgrade considerations → run the installer against the existing install → verify installation.
- **Upgrade (host OS + Mediator):** Back up logs → uninstall Mediator → upgrade host OS via leapp → reinstall Mediator → restore logs → reconnect ONTAP clusters.
