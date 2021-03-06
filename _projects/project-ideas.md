---
title: Project ideas
---
From time to time people want to write something, but can't think of something cool to write.

This is a list of projects that might be cool, or useful. Pick any idea and make it your own, or use
these to inspire you or something. Feel free to add your own ideas.

## Criterion++

C++ is lacking when it comes to nice open-source benchmarking tools. Kinda ridiculous when it is touted as good for writing
stuff when performance matters. It lacks something that goes beyond sticking things in a loop and surround it with calls
to `system_clock::now()`. Something that knows about confounding factors, and statistics, and stuff. Something that does
for C++ what [Criterion](http://www.serpentine.com/criterion/) does for Haskell.

## Documentation generator

Most documentation generators out there suck for C++ code in general. They usually try to have cross-language support,
and IMO that's a bad idea. It leads to supporting the lowest common denominator, and then they pretend certain
C++ concepts that would be nice in the documentation don't exist. An example of that is concepts, which are not
a formal C++ construct, but they are still used anyway. A tool geared specifically for C++ would have the best
C++ support, no? This would need some careful planning to decide what to support. [cppreference](http://cppreference.com)
might be a good case study.

## Snake

You know, the snake game. Lots of people in the Lounge are developing a snake game, each one on their own. You could give it a try too!

## IO design

Everybody complains about `<iostream>`. So why not let's try to fix it? Design an IO Stream library with
an interface you think would be useful and easier to work with. To completely replace `<iostream>`,
you would need to also replace some facets of localization/locales, but for now we'll just leave you
with the task of a good library for pulling in and pushing out bytes of data.

## TMP test framework

How does one write unit tests for traits? And what about testing when the feature is the fact that some
specific code fails to compile? It would be nice to have something for these situations. A simple thing
would repeatedly invoke the compiler and inspect is output. A more sophisticated thing would use libclang to parse the code.

## SO chat transcript scraper

A crawler to pull out history, and maybe a bot to keep it up to date in real-time.
Would enable a real search, and some maybe fun statistics at least.

## Audio router for Windows

The idea is to try to convince applications to use different audio devices based on
a global configuration (instead of relying on the app to know how to use a different sound card,
which most of non-audio-related things can't do). Would make things like listening to
music while streaming, but only streaming game audio much much easier.
