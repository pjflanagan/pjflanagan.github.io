---
layout: post
date: 2019-03-08
title: Metrocard Wireless Charger
description: A 3D printed wireless phone charger for standard size cards
categories: art
image: /assets/posts/2019/metrocard-phone-charger/header.jpg
github:
website: https://cad.onshape.com/documents/fe9a14ca0d7527d5d24e40f3/w/387d63da11f34da1257b0e9e/e/014e7bec234688533692fc05?fbclid=IwAR2KqT-QdLNaNoCOsT2Mom-XuLLP4sdTq22zFEmM5aI33Dw0zU4WSYTFZCU 
---

I've always been fascinated by the intersection of physical design and digital utility. Back in 2019, when wireless charging was starting to become a standard feature in smartphones, I decided to build a custom charging pad that looked like a piece of New York City history: a MetroCard.

## The Components

I started by sourcing the core electronics from a local shop called Tinkersphere. They carried DIY wireless charging kits that included the induction coil and the charging circuit board. Interestingly, the circuit board and coil together were almost exactly the same footprint as a standard MetroCard.

![Parts](/assets/posts/2019/metrocard-phone-charger/0-parts.jpg)

## Prototyping in Wood

Before committing to a 3D printed design, I built a wooden prototype using scrap wood, an Exacto knife, and hot glue. This helped me figure out the stacking height required to keep the coil close enough to the phone's surface for a stable connection.

I also made sure to align the status LED on the circuit board with the small hole in the corner of the MetroCard. This way, the card's own design served as the indicator light for the charger.

![Wood prototype plugged in](/assets/posts/2019/metrocard-phone-charger/1-1-wood-prototype.jpg)

## CAD Design with OnShape

This project was my first deep dive into **OnShape**, a browser-based CAD tool. Coming from a background in traditional AutoCAD, the parametric nature of OnShape was a learning curve, but it allowed me to precisely model the internal cavities for the electronics.

![CAD](/assets/posts/2019/metrocard-phone-charger/2-onshape.png)

The casing needed to be thin enough to not interfere with the induction field but strong enough to support the weight of a large phone. I designed it to be printed in two parts that would snap together around the MetroCard.

## The Final Build 

After receiving the 3D printed parts from a friend, I performed some light sanding and painted the casing with a matte black finish. This helped the plastic blend in with the black magnetic stripe of the card, giving it a much more "finished" look.

![Final build](/assets/posts/2019/metrocard-phone-charger/3-final.jpg)

## Lessons Learned

### Successes
The final build actually worked! It successfully charged my phone every night for several months. The status LED shining through the card hole was a particularly satisfying detail that made the project feel like a cohesive product rather than a science experiment.

### Challenges
The primary challenge was the "sweet spot." Wireless charging in 2019 was much more sensitive to alignment than the MagSafe systems we have today. Because the MetroCard is smaller than most phones, the device had to be perfectly centered, or it wouldn't charge. 

### Version 2 and Future Improvements
I've since updated the public model on OnShape to include a dedicated platform for the coil to prevent it from shifting over time. If I were to rebuild this today, I'd integrate magnets to help with phone alignment, effectively creating a "MetroSafe" charger.

You can view the updated CAD files [here](https://cad.onshape.com/documents/fe9a14ca0d7527d5d24e40f3/w/387d63da11f34da1257b0e9e/e/014e7bec234688533692fc05).
