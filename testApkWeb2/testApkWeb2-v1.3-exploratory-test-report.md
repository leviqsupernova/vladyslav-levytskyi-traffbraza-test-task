**ID:** ET04  
**Test Owner:** Vladyslav Levytskyi  
**Test Executor:** Vladyslav Levytskyi  
**Related Charter ID:** CH04  
**Test Date:** 22.12.2025  

**App:** Q Balloons  
**Version:** 1.3  
**Build:** N/A  
**SHA256:** 1eb429b8b9f0f3846a7717575b75f7ee45faeec20a16c4572f42120e74e8b46c  
**URL:** https://supergra.ua/uk  
**Environment:** OnePlus 8T, Android 14, security update August 5, 2024; Wi-Fi 1 GBit  

**Objective:** document the results of the exploratory testing of https://supergra.ua/uk in accordance with mini-charter CH04  

---

**Summary**

Due to the browser constraints, the target website was accessed via Google search. Since there was no way to verify the address was /uk, it was assumed UK localization version had to be tested, hence a UK VPN was used to trigger the (assumed) UK page to appear in Google search results. Once done, the VPN was turned off.  

The testing included multiple core user paths and flows on the website. It consisted of a Google account sign-up, navigation though bonuses, deposit menu, payment checkouts, accessing menus from the side bar and from homepage, tabs, in-game, as well as filtering and playing games, testing system integration points.  

---

**Defects found**

1. **Log in via Google account is blocked (00:22-00:24)**   

Trying to log in via an existent Google account through a Google button causes error 403: 'disallowed_useragent'.  

2. **Returning home from the system settings in 'Fortune of Olympus' doesn't trigger the function from the first tap; redirects to 'All Games' instead (05:28-05:36)**  

Redirect to home triggers only after multiple taps and redirects to 'All games' instead of homepage.  

 3. **'Glide for a Miracle' banner on the homepage is unresponsive upon touch (08:34-08:48)**  

The 'Glide for a Miracle' banner, both the image and button are unresponsive to touch.  

4. **An internal server error after changing the account password and tapping the sidebar burger menu button (10:16-10:27)**  

After the account password was changed, a tap on the sidebar burger menu caused numerous errors, one of which was captured post factum - status code 500: 'An internal server error occurred'.  

---

**Notes**

The website had significant performance deterioration throughout the session.  

---

**Test Assessment**

Common end user paths were tested. The defects found were reported. A performance issue was noted.  

---

**Suggested Actions**

Collect and analyze console/API logs of the reported defects. Compatibility, performance, regression testing is advised.  