# Tremola: Tic-Tac-Toe Extension

This project is a custom extension of **Tremola**, a decentralized, peer-to-peer messaging application developed by the University of Basel.

**My Key Contribution:**
I engineered a fully functional **Tic-Tac-Toe** game that runs directly within the chat interface, utilizing the underlying Secure Scuttlebutt (SSB) protocol for decentralized game state synchronization.

---

### Technical Implementation
I implemented a custom application-layer protocol on top of the Tremola/SSB messaging system.

* **State Serialization:**
  The game state is serialized into a 10-character string (e.g., `"3102001002"`) to minimize bandwidth over the mesh network.
  * *Digit 0:* Game Status (1=Start, 2=Invited, 3=Active, 4=Won, 5=Draw).
  * *Digits 1-9:* Board state (0=Empty, 1=Self, 2=Opponent).

* **P2P Synchronization Logic:**
  * **`update(newMessage)`:** Parses incoming P2P messages and updates the local state machine.
  * **`flipNumbers(number)`:** Implements a relative view system. Since the protocol is peer-to-peer, the opponent's "Self (1)" must be transformed into "Opponent (2)" locally before rendering.

* **Tech Stack:**
  * **Frontend:** JavaScript (WebView), HTML/CSS.
  * **Bridge:** Android `WebAppInterface` (Kotlin) to inject JavaScript state.

---

### Project Context
Developed as a semester project for the **Internet & Security** course (FS22) at the University of Basel.

* **Professor:** [Prof. Christian Tschudin](https://github.com/tschudin)
* **Team:** Mario Tachikawa, Erdem Koca.
* **Original Base Project:** [Tremola](https://github.com/cn-uofbasel/tremola)
* **Full Documentation:** See [README_TREMOLA.md](./README_TREMOLA.md) for the original setup and architecture details.
