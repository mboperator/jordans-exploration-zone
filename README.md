# BREACH POINT

A round-based tactical shooter that runs in the browser. One HTML file — every
texture, mesh, sound and animation is generated in code at load time. No art
assets, no audio files, no build step.

**Play:** https://mboperator.github.io/jordans-exploration-zone/

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
