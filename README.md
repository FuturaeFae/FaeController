# FaeController 1.0.0

FaeController is the standalone Windows/Linux host service and administrator web controller for the Fae Minecraft ecosystem. This is a clean product line; it does **not** migrate a previous host-service installation.

## Independence contract

FaeController must be fully useful without Minecraft-side Fae plugins: server lifecycle, console/logs, files, metrics, native Players, native Backups, native Schedules, marketplace, host operations and federation are Controller-owned. Conversely, FaeCore and every Fae Minecraft plugin must remain usable without FaeController. Shared functionality may exist on both sides when that is necessary for this two-way independence. Plugin-specific gameplay data/actions remain owned by the corresponding plugin and can optionally appear in FaeController through typed FaeCore/FaeNetwork extension contracts.

## Servers and lifecycle

Create Server creates a blank Paper/Purpur/Folia/Velocity runtime; it does not auto-install Fae plugins or profiles. Import Server registers an explicit existing root. Clone Server is a separate stopped-boundary operation with Clean and Full modes; clones receive a new server identity and collision-free port and do not copy Controller credentials. EULA acceptance remains a server Console/detail action. Server processes are direct children of the Controller service and are protected from root/Administrator Minecraft launches.

## Files and revisions

Host/server files use an Explorer-style browser with Back/Forward/Up, address/search, navigation pane, selection, drag/copy/move, rename, upload/download, Recycle Bin and keyboard shortcuts. Text/config saves create durable FaeController revisions. Revision history can be listed and restored even after the browser session ends. Session Undo/Redo remains separate.

## Players without plugins

The native Player service reads known identities from server files and derives online counts using the Minecraft server-list status protocol when possible, with latest.log parsing as a fallback. The Controller Player Manager exposes identities, profiles, FaeUser ownership linking, stats/leaderboards, achievements/history, preferences, unlocks/selections, punishments, sessions/playtime, Bedrock appearance data and privacy operations. This does not make FaeCore depend on FaeController: FaeCore keeps equivalent standalone player contracts for plugin consumers.

## Backups

Native backups support content-defined deduplication, compression, verification, retention/GC, granular/full staged restore, multiple named repositories and mirrors, local/mounted paths or repositories hosted by another enrolled FaeController. AES-256-GCM encryption is toggleable. Existing repository data is atomically migrated and deep-verified when encryption changes. Encrypted repositories use FaeController recovery authorities; no operator-held recovery password is required. A surviving repository host can authorize a fresh Controller and perform Original Host Lost Recovery. Local Safety Snapshot remains a separate emergency ZIP-style preservation path.

## Schedules and stopped-boundary changes

FaeController owns durable Basic/Cron/After-task timing, retries, misfires, chaining, scopes and federation. `NEXT_STOP` changes execute after every successful normal or force stop; `NEXT_RESTART` changes execute at restart. Optional Minecraft-domain actions are dispatched to the owning plugin through FaeCore/FaeNetwork without moving that domain authority into FaeController.

## Federation and extensions

STANDALONE is the default. PRIMARY can enroll SECONDARY FaeController hosts. Physical host operations execute on the owning Controller. Player APIs and typed plugin extension modules/actions are federated to the owning host. SSH is optional and used only for Host Consoles, not normal federation.

## Connectivity and security

FaeController discovers interfaces, STUN/public-IP observations and read-only PCP/NAT-PMP/UPnP capability signals, distinguishes observed/advertised/verified endpoints and never labels an observed public IP reachable without external proof. Anonymous `/api/v1/health` is deliberately minimal and does not disclose the version. Accounts use hashed passwords, HttpOnly sessions, Remember Me token rotation/invalidation and scoped GLOBAL/HOST/SERVER_GROUP/SERVER grants.

## Marketplace and deployments

Modrinth/Hangar browsing supports exact compatible versions, including downgrades. Auto-update has both a server master toggle and per-plugin toggle. Only JARs installed/tracked by FaeController's marketplace are managed; manually installed/untracked JARs are untouched. Fleet Deployments provide preview, canary, stopped-boundary staging, verification and rollback. The Plugins tab includes a clean **Pending Changes** list showing marketplace and other staged plugin-JAR installs/updates/removals with their lifecycle trigger.

## Store/commerce decision

The Fae ecosystem has **no public online storefront**. FaeStore remains an in-game economy-backed shop plugin; real-money/public-web commerce is not part of the current plan.

## Installation

The Linux installer supports systemd, OpenRC, runit and SysV. Windows supports x64 and ARM64 and uses a Job Object service wrapper. FaeController 1.0.0 is a fresh FaeController installation. Future FaeController-to-FaeController installer upgrades detect `installation.json` and preserve the existing federation role/configuration, servers, backups, secrets and **all Controller accounts** (password hashes, roles, permissions and scoped grants) unless the operator explicitly changes a setting. The installers verify that pre-existing account records survive an upgrade. Uninstall removes service/binaries by default and preserves durable data; purge is explicit.
