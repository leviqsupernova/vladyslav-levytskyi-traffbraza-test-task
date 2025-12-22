**ID:** ET03  
**Test Owner:** Vladyslav Levytskyi  
**Test Executor:** Vladyslav Levytskyi  
**Related Charter ID:** CH03  
**Test Date:** 22.12.2025  

**App:** Q Balloons  
**Version:** 1.3  
**Build:** N/A  
**SHA256:** 2958e1362fae0615f0e835f0d3a7c7b48a7c1fd0518b2a731fd4b832b0d9e0ee  
**URL:** https://supergra.ua/uk  
**Environment:** OnePlus 8T, Android 14, security update August 5, 2024; Wi-Fi 1 GBit  

**Objective:** document the results of the exploratory testing of https://supergra.ua/uk in accordance with mini-charter CH03  

---

**Summary**

Due to the browser constraints, the target website was accessed via Google search. Since there was no way to verify the address was /uk, it was assumed UK localization version had to be tested, hence a UK VPN was used to trigger the (assumed) UK page to appear in Google search results. Once done, the VPN was turned off.  

The testing included multiple core user paths and flows on the website. It consisted of a Google account sign-up, navigation though bonuses, deposit menu, payment checkouts, accessing menus from the side bar and from homepage, tabs, in-game, as well as filtering and playing games, testing system integration points.  

---

**Defects Found**

1. **Orientation change redirects to google.com (03:16-03:20)**  

Screen orientation change crashes the website and triggers homepage, that is google.com, to open up.  

2. **'4 Pots of Egypt' demo start shows compatibility error (03:43-03:47)**  

Tap on 'Demo' under '4 Pots of Egypt' summons error 'This game is not optimised for your browser. For a better experience, Use Chrome 50+, Android 8.0+'.  

3. **'Mr. First' demo start results in error 500 (04:36-04:42)**  

Tap on 'Demo' under 'Mr. First' summons status code 500 error: 'internal server error'.  

4. **Returning home from the system settings in 'Fortune of Olympus' doesn't trigger the function from the first tap; redirects to 'All Games' instead (06:10-06:17)**  

Redirect to home triggers only after multiple taps and redirects to 'All games' instead of homepage.  

5. **'Glide for a Miracle' is unresponsive (09:39-09:48)**  

No visible function is triggered after tapping 'Glide for a Miracle'.  

---

**Notes**

> No additional notes.

---

**Test Assessment**

Common end user paths were tested. The defects found were reported.  

---

**Suggested Actions**

Collect and analyze console/API logs of the reported defects. Compatibility and regression testing is advised.  
