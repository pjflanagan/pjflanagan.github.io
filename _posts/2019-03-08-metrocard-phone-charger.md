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

I used to have a phone with wireless charging enabled. I wanted to take advantage of that feature, and thought maybe I could build a charging pad myself.

## The Components

I started by sourcing the core electronics from a local shop called [Tinkersphere](https://tinkersphere.com/?srsltid=AfmBOor8ARWSNdzautG6-89ryuLN330dKMfUL9zv6uuKVnx3-rjUNzv_). They carried the induction coil preconfigured with a circuit board and indicator light. Interestingly, the circuit board and coil together were almost exactly the same footprint as a standard MetroCard.

![Wireless charging component on top of a MetroCard](/assets/posts/2019/metrocard-phone-charger/0-parts.jpg)

## Prototyping in Wood

Before committing to a 3D printed design, I built a wooden prototype using scrap wood, an Exacto knife, and hot glue. This helped me figure out the stacking height required to keep the coil close enough to the phone's surface for a stable connection.

I also made sure to align the status LED on the circuit board with the small hole in the corner of the MetroCard. This way, the card's own design served as the indicator light for the charger.

![Wood prototype plugged in with light positioned near MetroCard hole](/assets/posts/2019/metrocard-phone-charger/1-1-wood-prototype.jpg)

## CAD Design with OnShape

This project was my first deep dive into [OnShape](https://www.onshape.com/en/), a browser-based CAD tool. I had some experience using AutoCAD, so learning how to use OnShape wasn't terribly difficult.

![CAD design of idealized card charger (this is not what I printed)](/assets/posts/2019/metrocard-phone-charger/2-onshape.png)

The casing needed to be thin enough to not interfere with the induction field, so I didn't get it a top. The sides had to be strong enough to support the weight of a phone, which wasn't a whole lot. 

## The Final Build 

After receiving the 3D printed parts from a friend, I performed some light sanding and painted the casing black. This helped the plastic blend in with the black magnetic stripe of the card, giving it a much more "finished" look. Otherwise it would have been an unsightly green.

![Final build sitting on my desk](/assets/posts/2019/metrocard-phone-charger/3-final.jpg)

## Lessons Learned

### Successes

The final build worked great. It successfully charged my phone during work. The status LED shining through the card hole was a particularly satisfying detail that made the project feel like a cohesive product rather than a science experiment.

### Challenges

The primary challenge was the "sweet spot." Wireless charging in 2019 was much more sensitive to alignment than the MagSafe systems we have today. Because the MetroCard is smaller than most phones, the device had to balance somewhat precariously. This wireless charger also got pretty hot while charging. 

### Version 2 and Future Improvements

I've since updated the public model on OnShape to include a dedicated platform for the coil so it doesn't have to be taped to the underside of the card. If I were to rebuild this today, I'd integrate magnets to help with phone alignment. I'd call it the "MetroSafe" charger.

You can view the [updated CAD files on OnShape](https://cad.onshape.com/documents/fe9a14ca0d7527d5d24e40f3/w/387d63da11f34da1257b0e9e/e/014e7bec234688533692fc05).
