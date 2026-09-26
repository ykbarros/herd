# Herd

Think like everyone else to win. A phone-friendly party game with two games in one:

- **Herd Mentality:** everyone answers the same question in secret. Everyone with the single most popular answer gets a cow.
  If exactly one player is alone with their answer, they get the pink cow, and you can't win while holding it. First to 8 cows wins (or 5 or 10).
- **Green Team Wins:** fill in the blank, this or that, and multiple choice questions. Everyone with the most popular answer joins the Green Team:
  +1 for joining, +2 for staying. Everyone else goes Orange. Most points after 15 rounds wins (or 9 or 21).

In both games, if two answers tie for most popular, nobody scores (nobody goes Green).

Typed answers are grouped automatically, ignoring capital letters, punctuation, "the/a" and plurals. Before scoring, the host can merge groups
that mean the same thing ("Coke" and "Coca-Cola"): tap one group, then tap the group it belongs with.

## Two ways to play
- **One phone:** pass it around and answer in secret.
- **Rooms:** the host taps *Start a room* and shares the 4-letter code or invite link. Everyone answers on their own phone.
  Rooms are peer-to-peer (WebRTC via [PeerJS](https://peerjs.com/)), so there's no server to run.
  The host's phone runs the game, so the host keeps Herd open. The host can answer for anyone who goes offline, or remove them from the game.

A single self-contained `index.html` with no build step. One-phone mode works offline once loaded.

## Dev notes
- `?net=local` swaps PeerJS for a same-browser BroadcastChannel transport, so you can play a room across several tabs with no internet.
- `?peerhost=127.0.0.1:9000` points PeerJS at a self-hosted PeerServer (`npx peer --port 9000`).
- Decks live at the top of the first `<script>` in `index.html`, one question per line.
  Herd Mentality questions are plain lines, fill in the blank uses `___`, and choice questions are `Question|Option A|Option B[|C|D]`.
