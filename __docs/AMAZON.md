# Amazon Affiliate Implementation for flanny.app

Since you've signed up for Amazon Associates, here is how to integrate links into your Jekyll-based blog and apps.

## Add links to Blog
The fastest way to add a link is using standard Markdown. Use your **Amazon SiteStripe** (the bar at the top of Amazon.com) to get a "Text" link.

```markdown
I bought a [Nuphy Halo](https://amzn.to/YOUR_SHORT_LINK), and I love it.
```

```markdown
{% include amazon-link.html url="https://amzn.to/YOUR_LINK" name="Nuphy Halo Keyboard" %}
```



## Potential Products to Link
Based on your current blog posts, here are specific products you should consider linking:

*   `_posts/2024-10-01-keyboards.md`: Link the Nuphy Halo and Keychron switches.
*   `_posts/2025-11-12-garmin-chinese-watchface.md`: Link the specific Garmin watches.

### Mechanical Keyboards (`_posts/2024-10-01-keyboards.md`)
*   **Keychron K2:** The "gateway" keyboard you won.
*   **NuPhy Halo 96 / 75:** Your current favorite "bag of marbles" keyboard.
*   **Switches:** Gateron Red/Brown/Blue switches.
*   **Modding Supplies:** O-rings, Keyboard Foam, and Krytox Lubes.
*   **3D Printers:** (Since you mentioned wanting one) Creality Ender 3 or Bambu Lab A1.

### Garmin & Running (`_posts/2025-11-12-garmin-chinese-watchface.md` etc.)
*   **Garmin Forerunner 255/265:** Great mid-range training watches.
*   **Garmin Fenix 7 / Epix:** High-end models for "Asian art" watch faces.
*   **Running Gear:** Aftershokz bone-conduction headphones, running vests.

### GoPro & Photography (`_posts/2020-12-23-nightpro-for-gopro.md`)
*   **GoPro HERO 12/11 Black:** The core camera for NightPro.
*   **Mini Tripods:** Manfrotto PIXI or Joby GorillaPod (essential for nightlapses).
*   **High-Speed SD Cards:** SanDisk Extreme Pro (required for 4K video).

### Electronics & DIY (`_posts/2019-03-08-metrocard-phone-charger.md` etc.)
*   **Wireless Charging Kits:** DIY induction coils and circuit boards.
*   **Soldering Tools:** Pinecil Portable Soldering Iron or Hakko stations.
*   **Arcade Parts:** Sanwa Joysticks and Buttons (for the Arcade Cabinets post).

### Rollerblading (`_posts/2022-07-01-rollerblade-bag.md`)
*   **FR Skates / Powerslide:** High-quality urban skates.
*   **Rollerblade Bags:** Specialized backpacks for carrying skates.
*   **Bearings:** Bones Reds or Twincam bearings.

### Blackjack & Gaming (`_posts/2018-02-03-blackjack-simulator.md`)
*   **Premium Playing Cards:** Theory11 or Bicycle Architectural decks.
*   **Card Shufflers:** Automatic 6-deck shufflers for home practice.
*   **Blackjack Strategy Cards:** Physical plastic cards for quick reference.
*   **Books:** *Bringing Down the House* (the MIT Blackjack story).

### Dune & Sci-Fi (`_posts/2021-12-19-gom-jabbar.md`)
*   **The Books:** *Dune* Deluxe Edition (hardcover).
*   **Dune: Imperium:** The board game (very popular and high-rated).
*   **Movie Merch:** Art and Making of Dune books.

### MTA Clock & Electronics (`_posts/2020-04-28-mta-clock.md`)
*   **Microcontrollers:** Arduino Nano, ESP8266 (Wemos D1 Mini).
*   **Servo Motors:** SG90 Micro Servos (the "better" alternative for the clock).
*   **Jump Wires & Breadboards:** Essential for prototyping.
*   **Soldering Stations:** Hakko FX-888D or entry-level kits.

### Cat Toys & Robotics (`_posts/2020-05-13-cat-laser.md`)
*   **Laser Diodes:** 5V laser modules for Arduino.
*   **Pan-Tilt Kits:** Dual-axis servo mounts.
*   **Interactive Cat Toys:** Automatic laser towers (for those who don't want to build one).

### Mandarin Study (`_posts/2025-09-27-study-mandarin.md`)
*   **Textbooks:** *Integrated Chinese* or *A Course in Contemporary Chinese* (Taiwan).
*   **Zhuyin Keyboards:** Silicone keyboard covers with Zhuyin/Bopomofo.
*   **Writing Practice:** Water-tracing cloth for character practice.

### Running & Fitness (`_posts/2012-03-05-run-calculator.md`)
*   **Shoes:** Recommendations for popular brands (Brooks, Saucony, Hoka).
*   **Massage Tools:** Foam rollers, Theragun/massage guns for recovery.
*   **Hydration:** Handheld bottles or running belts.
*   **Books:** *Born to Run* or *Finding Ultra*.
