# Make Vandy Great Again Poker

Private 4-card Pot-Limit Omaha for up to six friends using **virtual chips only**. No deposits, withdrawals, or cash prizes.

## Quick local test
1. Install Node.js 20 or later from https://nodejs.org/
2. Open a terminal in this folder.
3. Run `npm install` then `npm start`.
4. Open http://localhost:3000 in a browser.

## Publish online using GitHub + Render
1. Make a free GitHub account at https://github.com and sign in.
2. Create a **new repository** called `make-vandy-great-again-poker`. You can set it to private.
3. Upload **the contents of this folder** to the repository root, including `server.js`, `package.json`, `render.yaml`, and the `public` folder. Commit the files. (Do not upload only the ZIP.)
4. Go to https://dashboard.render.com/ and sign in with GitHub.
5. Select **New > Web Service**, connect GitHub if prompted, and select your repository.
6. Configure: Language/Runtime `Node`; Build Command `npm install`; Start Command `npm start`; instance type `Free` if offered. Or use **New > Blueprint** and point it at the repository's `render.yaml`.
7. Click **Deploy Web Service** and wait until Render reports that the service is live.
8. Open the public `https://...onrender.com` URL that Render assigns. This is your actual website link; it cannot be known before deployment.
9. Enter a nickname, select **Create table**, then use **Copy invite link** to share with friends. Friends enter their nicknames and choose **Join table**.

### Important notes
- On free hosting, the site may sleep when inactive, causing a delay when waking up. Availability and free-tier limits can change.
- The server keeps rooms in memory. Deploys/restarts erase tables and chip balances.
- Players who disconnect during a hand are folded. Rejoining requires a new seat when the hand finishes.
- No user authentication or persistence. Room links should be shared privately.
- This is a starter project. Betting/side-pot logic needs multiplayer edge-case testing before treating it as a polished poker game.
- Dealing is random; no secret host-favored outcomes are implemented.

## Play-money buy-ins and chip denominations

The host selects a $20 or $40 **virtual** buy-in when creating a room. Everyone joining receives that same starting stack. Internal chip balances use integer cents. Blinds are $0.25/$0.50; bets increase in $0.25 increments. The interface displays chip breakdowns in $5, $1, and 25-cent denominations. No payment integration or cash-out is included.

## Virtual rebuys

When a player reaches $0, they can select **Rebuy $20** or **Rebuy $40** between hands. Rebuys add virtual chips only; there are no transactions, withdrawals, or prizes. Players with remaining chips cannot rebuy. The host may start the next hand once at least two connected players have chips.
