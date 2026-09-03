# Jordan's Exploration Zone

Browser games that build themselves. Each one is a single HTML file — every
texture, mesh, sound and animation is generated in code at load time. No art
assets, no audio files, no build step.

**Play:** https://mboperator.github.io/jordans-exploration-zone/

| Game | What it is |
|---|---|
| [BREACH POINT](breach-point.html) | Round-based tactical shooter, 3v3, with P2P multiplayer |
| [Krusty Krab Escape](krusty-krab-escape.html) | First-person survival-horror escape |

---

# BREACH POINT

A round-based tactical shooter that runs in the browser.

## Controls

| | |
|---|---|
| Move | `W` `A` `S` `D` |
| Look | Mouse (click the page to capture it) |
| Fire | Left mouse |
| Aim down sight | Right mouse |
| Walk quietly | `Shift` |
| Crouch | `Ctrl` / `C` |
| Jump | `Space` |
| Reload | `R` |
| Primary / sidearm | `1` `2` |
| Plant / defuse | Hold `F` |
| Buy menu | `B` (buy phase only) |
| Scoreboard | Hold `Tab` |
| Pause | `Esc` |

## The game

First to 5 rounds, 3v3. You attack rounds 1–4 carrying the breacher — reach the
site, hold `F` for 4 seconds to plant, then survive 45. Then you swap to
defending, where you stop the plant or defuse it in 7 seconds. Wiping the other
team also takes the round. Credits carry over, so buy the good gun.

Bot difficulty runs 1–10 on the main menu. Reaction time, aim error, damage,
burst length and aggression all scale across the range; level 5 is a fair fight.

## Multiplayer

Peer-to-peer over WebRTC with 6-character join codes — no server to run. The
public PeerJS broker handles introductions only; after that the browsers talk
directly. Three modes: **Duel** (1v1 deathmatch), **Team** (up to 3v3, bots fill
empty slots) and **Co-op** (everyone versus the bots).

Each peer owns its own operator and the host owns the shared world, so nothing
waits on a round trip before you move or shoot. It trusts the other clients,
which is the right trade for a game you play with people you handed a code to.

Needs an internet connection even on a LAN, and a strict NAT can block the
direct connection.

## Built with

[Babylon.js](https://www.babylonjs.com/) for rendering and
[PeerJS](https://peerjs.com/) for the networking. Both from a CDN; nothing else.

---

# Krusty Krab Escape

You are locked in the Krusty Krab after closing and SpongeBob is hunting you
with a spatula. **One hit ends the run** — there are no hearts and no respawn.

## Controls

| | |
|---|---|
| Move | `W` `A` `S` `D` |
| Look | Mouse (click the page to capture it) — arrow keys also turn |
| Sprint | Hold `Shift` — costs stamina, and it's loud |
| Crouch | `C` — slow and silent |
| Interact | `E` — pick up, unlock, hammer, plank, work the safe, free Patrick |
| Fire the bubble gun | Left mouse / `F` |
| Hold a key | `1` `2` `3` `4` colour keys, `5` white key |
| Tools | `6` hammer, `7` plank, `8` bubble gun |
| Shop | `B` from the title |
| Mute / restart | `M` / `R` |

## The game

Six zones behind colour-locked doors. Keys are **consumed** — one key, one door,
and the padlock visibly breaks off. A hammer smashes boarded doorways, a single
plank bridges two grease pits and can be pried back up, and Mr. Krabs' safe holds
the **white key** behind a three-digit combination scattered across three notes
and randomised every run.

The white key doesn't open the exit. It frees **Patrick**, and the moment his
chains hit the floor the front doors unbolt, the lights go red and SpongeBob goes
permanently enraged. Then you hammer through four boards with him closing on you,
and you don't leave without Patrick.

The tension isn't the chase — SpongeBob is slower than you walk. It's that
hammering, planking, working the dial and freeing Patrick all root you in place
and make noise.

## Escaping pays

Every escape is worth 5 Krusty Bucks on any difficulty, saved to `localStorage`,
spent in the shop on **36 skins** covering the cast. Your skin shows up in the
corner badge, which walks when you walk.

## Built with

Nothing. It's a hand-written raycaster — DDA wall casting, a per-column z-buffer,
box-model 3D characters on a forward-kinematics walk rig, procedural textures and
a Web Audio synth. One file, no dependencies, no network calls.
