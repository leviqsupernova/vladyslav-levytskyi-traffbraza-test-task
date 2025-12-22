# **Egg Secret v1.0 Exploratory Test Report**

**ID:** ET02  
**Test Owner:** Vladyslav Levytskyi  
**Test Executor:** Vladyslav Levytskyi  
**Related Charter ID:** CH02  
**Test Date:** 22.12.2025  

**Application:** Egg Secret  
**Version:** 1.0  
**Build:** N/A  
**SHA256:** c6bc6b84aa04a0ef3970931468f472bf012af85b1b9ec0bd73a2ecdf50b3e4a2  
**Environment:** OnePlus 8T, Android 14, security update August 5, 2024; Wi-Fi 1 GBit  

**Objective:** document the results of the exploratory testing of Egg Secret v1.0 in accordance with mini-charter CH02  

---

**Test Table**

| Module/Feature     | Actions                                                                                                                                                                                                                                                                                                                                           |
| ------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Baskets/Game Loop  | Observed game start without interruption. Tapped the baskets slowly, quickly, repeatedly. Tapped the baskets right after the game start. Tapped multiple baskets at the same time. Tapped a basket with a single chicken if > 1 is present and waited for the timer to expire. Tapped all available chickens. Tapped on eggs of different colors. |
| HUD                | Tapped the home, pause, settings buttons mid-game.                                                                                                                                                                                                                                                                                                |
| Score/Calculations | Verified correctness of the score logging.                                                                                                                                                                                                                                                                                                        |
| Timer              | Observed the timer when idle, playing, after screen rotation, accessing Settings, main menu, terminating and minimizing the app, switching processes, using Android volume buttons.                                                                                                                                                               |
| Settings           | Accessed the settings from the main menu and mid-game, changed the settings, checked if the settings are respected by the game after terminating and minimizing the app, switching processes, using Android volume buttons, playing, switching between the game screens.                                                                          |
| System integration | Checked the app's functionality after terminating and minimizing the app, switching processes, using Android volume buttons, changing screen orientation.                                                                                                                                                                                         |

---

**Defects Found**


1. **Inconsistent number of chickens per round, up to no chickens at all (00:04-00:06, 00:33-00:35, 00:29-00:32)**  

The game allows a different number of chickens each round up to no chickens at all.  

2. **A successful uncover of all the chickens while the time allows still ends up with a lose (00:33-00:41)**  

It's impossible to win a round even when all the chickens have been uncovered.  

3. **Mid-game screen rotation resets the settings and redirects back to the main screen (00:44-00:56)**  

The rotation of the screen resets the saved game data.  

4. **Rotation scales UI incorrectly and blocks the view of the UI elements (00:51-01:00)** 

Screen rotation scales the background incorrectly and blocks the 'Exit' button in the main menu.  

5. **Returning from the settings mid-game redirects to the main screen and resets the game instead (01:18-01:21)**  

Accessing the settings menu mid-game resets the saved game data.  

6. **The timer delays, may change pace, and freezes at different timer values (01:41-02:37, 04:29-04:42)**  

The time may delay its countdown and gradually lose pace, eventually stopping at a the end of the countdown (10-20%). Changing screen orientation makes the timer start off rapidly.  

7. **Chicken icons mismatch (02:50-03:07)**  

Selecting chicken type 1 in the settings changes the in-game chicken icon to type 2, type 2 to type 3, type 3 to type 1, both under the baskets and results pop-up.  

8. **The app termination and re-launch resets the settings (04:42-04:50)**  

The data is reset again upon app full re-launch.  

9. **Process switch doesn't respect the in-game settings (05:13-05:24)**  

After process switch, the settings state is visually saved (music turned off), but the music starts playing again.  

---

**Notes**

Although the test was functional, several UI/UX observations were made.  

**UI/UX:**  

- Fonts, UI elements, margins have inconsistent styling
- Localization may require minor revision
- Basket animation glitches out each round based on the last touched basket (03:46-03:51, 04:02-04:04)

---

**Test Assessment**

All visible functionality was tested. Defects are clustered in the game loop, timer, and at the system integration points.  

Occasional UI/UX notes were made.  

---

**Suggested Actions**  

Verify the reported functional defects and review the UI/UX observations with the team.  
