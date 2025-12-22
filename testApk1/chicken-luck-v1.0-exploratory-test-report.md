# **Chicken Luck v1.0 Exploratory Test Report**

**ID:** ET01  
**Test Owner:** Vladyslav Levytskyi  
**Test Executor:** Vladyslav Levytskyi  
**Related Charter ID:** CH01  
**Test Date:** 22.12.2025  

**Application:** Chicken Luck  
**Version:** 1.0  
**Build:** N/A  
**SHA256:** 8998c861ff50209a6bd823e6cd9b409e1dea7be489b3060fad8b76aecc5eb72c  
**Environment:** OnePlus 8T, Android 14, security update August 5, 2024; Wi-Fi 1 GBit  

**Objective:** document the results of the exploratory testing of Chicken Luck v1.0 in accordance with mini-charter CH01  

---

**Test Table**

| Module/Feature                  | Actions                                                                                                                                                                                                                                                                                                                                                                                       |
| --------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Bet/Cashout                     | Observed game start without interruption. Placed the default bet 1. Placed the predefined bets 2, 5, 7, 10 via buttons. Changed the bet value via the minus and plus signs. Bet 0, bet max. Bet at the timer values 10 and 1. Bet when stars < bet amount. Bet module buttons used with quick taps. Tapping to overflow the edge values. Tried to cashout upon pressing on a walking chicken. |
| Multiplier/Calculations/Stars | Calculated various multipliers. Stacked multipliers. Tried to add stars via the star icon and plus sign nearby.                                                                                                                                                                                                                                                                               |
| Timer                             | Bet at different timer count, including edge values. Tapped on the timer container.                                                                                                                                                                                                                                                                                                           |
| Settings                          | Opened the settings. Changed the name and profile picture. Pressed 'Highest Score', 'Share this app', 'Rate us', 'Bonus is not ready'. Tapped on the reset bonus container. Delete data. Go back.                                                                                                                                                                                             |
| System integration                | Opened the app after minimizing, changing active processes, terminating. Used the app after using Android volume buttons. Tried to test landscape orientation.                                                                                                                                                                                                                                |

---

**Defects Found**

1. **Multiplier not reflected on the screen upon auto cashout (00:13-00:18)**  

 A multiplier indicator appears on the multiplier history bar and remains throughout the run each time a player makes a cashout with a tap, but not when the cashout is made automatically after the timer expires.  

2. **Incorrect rounding made upon cashout (00:32-00:35)**  

The bet value was 3, while the multiplier was x1.3. The result, 3.9, was rounded incorrectly to 3 instead of 4.  

3. **Multiplier indicators don't appear/scale the section to fit if there's no space left (01:21-01:25)**  

 If the multipliers history bar is already filled out, further multipliers are either not reflected, or overflow the visible screen space instead of scaling the section.  

4. **Cashout at x0.0 multiplier still gives stars (04:11-04:15)**  

The bet of 88 was multiplied by x0.0. Instead of 0, the game granted 57 stars which were added to the balance accordingly.  

5. **If the balance is > 0, but < than the bet which had been previously selected, the game allows placing the bet (04:51-05:09)**  

The selected bet value remains 97, while the stars balance is 81. The bet then is still placed again and the score is multiplied and reflected in the stars balance accordingly.

---

**Notes**

Although the test was functional, a sheer number of UI/UX and product observations were made.  

**UI/UX:**

- Absence of onboarding made the first interaction confusing
- Win/lose screen duration may be too short; the lose screen uses a green color, which gave an impression of a win
- Notification 'It remains until the next bonus ... ' is confusing and grammatically incorrect 
- 'New round starts after' is grammatically incorrect in the given context
- Placement of the bonus related button and container in the settings seemed inappropriate. It was also unclear why they change color upon touch, but no action or notification is triggered
- The buttons throughout the game use inconsistent capital letter convention (e.g., 'Highest Score' and 'Rate us')
- Fonts, UI elements, margins have inconsistent, mockup styling
- Localization may require deep revision

**Product:**

- The star balance icon could be made active, as it will likely make players exposed to a hypothetical stars shop window more often
- Even correct rounding may feel unsatisfactory to users, as fractional discards change the perceived fairness; in-game currency with decimals support can improve it and reduce thematic disconnect between stars and a farm setting 
- Bet amount slider could be of use, as changing a bet via the minus and plus sign buttons was tedious

---

**Test Assessment**

All visible functionality was tested. Defects clustered in the bet, multiplier/calculations/stars modules are found and reported.  

Occasional UI/UX and product notes were made.  

---

**Suggested Actions**

Verify the reported functional defects and review the UI/UX, product observations with the team.  
