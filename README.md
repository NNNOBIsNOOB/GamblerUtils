# CasinoUtils

**CasinoUtils** is a 100% client-side Fabric mod for **Minecraft 1.21.11** designed for economy and casino streamers on servers like DonutSMP. Built with Java 21 and native Yarn mappings, author **4cya**.

![CasinoUtils Banner](src/main/resources/assets/casinoutils/icon.png)

---

## Features

### 1. DonutSMP Streamer Dashboard GUI (`/cu gui` or `K`)
- **Visual Architecture**: Sleek dark-panel streamer dashboard inspired by DonutSMP Streamer Utilitys (`#0E1117` obsidian background, `#161B26` elevated cards, `#263042` crisp borders, electric cyan `#38BDF8`, emerald profit `#22C55E`, crimson loss `#EF4444`, and gold `#F59E0B`).
- **5 Integrated Tabs**:
  1. **Dashboard & Queue**: Real-time volume in, total paid out, and net profit cards, scrollable queue cards with player skin head avatars (`PlayerSkinDrawer`), VIP/Tag badges, and per-row `[Pay]` and `[Pop]` buttons.
  2. **AH / Live Bidding**: 48x48 scaled item pedestal (`scale(2.5f)`), held item selector, 18-slot inventory-style clickable item search grid, timer progress bar, and highest bidder avatar.
  3. **Giveaway Wheel**: Live 2D miniature animated spinning wheel drawn natively using `DrawContext` with 8 slice colors, top pointer needle, and instant winner payout pre-filling.
  4. **Safety & VIPs**: Configurable confirm threshold, daily stop-loss, owed rakeback payout list, and VIP toggles.
  5. **Config & OBS**: OBS server port, chat presets (DonutSMP vs Generic), 1-click stream overlay URL copy buttons, and **Dual Discord Webhooks**.

### 2. Live OBS Stream Overlays (Built-in HTTP Server)
Powered by an asynchronous, ultra-low-latency built-in HTTP server (default port `8765`):
- `http://127.0.0.1:8765/queue` — Transparent payment queue overlay with avatar heads.
- `http://127.0.0.1:8765/profit` — Net profit/loss ticker overlay.
- `http://127.0.0.1:8765/cu/ah` — Live auction bidding overlay with item icons, bidder skin, progress bar, and 10-second auto-hide after round ends.
- `http://127.0.0.1:8765/cu/gw` — Animated 60 FPS HTML5 Canvas spinning wheel with physics bounce, ease-out spin animation, confetti, and auto-reset.

### 3. Dual Discord Webhooks
- **Audit Webhook**: For CSV session exports and periodic summary embeds.
- **Dedicated Live Profit/Loss Webhook**: Creates a pinned embed card in your Discord channel that live-updates every time bets, payouts, or giveaways occur. Falls back automatically to the audit webhook if blank.

### 4. In-Game Mini HUD Overlay (`/cu hud`)
- Lightweight, translucent obsidian overlay in the top-left corner (`8, 8`) displaying:
  * Brand header + live net profit/loss.
  * Active queue status: `#1 <player> ($Amount)`.
  * Live auction or giveaway status.
- Registered with modern 1.21.11 `HudElementRegistry`.

---

## Commands

| Command | Description |
|---|---|
| `/cu gui` | Opens the CasinoUtils Streamer Dashboard GUI |
| `/cu hud` | Toggles the in-game mini HUD overlay on/off |
| `/cu next` | Pops the next player from the payment queue |
| `/cu lever` | Toggles automatic queue advance on lever flick |
| `/cu reset` | Resets session profit/loss and clears queue |
| `/cu status` | Prints full session financials to chat |
| `/cu ah start <sec> <minBid> <item>` | Starts a live countdown auction |
| `/cu ah stop` | Stops the active auction and declares winner |
| `/cu ah testbid [amount]` | Simulates a test bid for testing overlays |
| `/cu gw start <cost> <maxTix> <prize>` | Opens giveaway for entries via `/pay` |
| `/cu gw spin` | Spins the wheel and selects cryptographically weighted winner |
| `/cu gw stop` | Stops/resets giveaway and clears entries |
| `/cu vip <player>` | Toggles VIP status for a player |
| `/cu tag <player> [tag]` | Sets a custom tag for a player |
| `/cu rakeback <player>` | Pre-fills owed rakeback payout |
| `/cu export csv` | Exports audit ledger to CSV file |
| `/cu webhook summary` | Sends session financial report embed to Discord |
| `/cu webhook set <url>` | Sets the Discord audit webhook URL |
| `/cu webhook live toggle` | Toggles real-time Discord P&L updates |
| `/cu webhook live set <url>` | Sets dedicated Live Profit/Loss Discord webhook |
| `/cu webhook live clear` | Clears dedicated Live P&L webhook (falls back to main) |

---

## Building from Source

Requires **Java 21**:

```bash
git clone https://github.com/4cya/CasinoUtils.git
cd CasinoUtils
./gradlew build
```

The compiled mod JAR will be output to:
```
build/libs/casinoutils-1.0.0.jar
```

Place `casinoutils-1.0.0.jar` into your Minecraft `.minecraft/mods` directory alongside **Fabric Loader 0.18+** and **Fabric API**.

---

## License

This project is licensed under the MIT License.
