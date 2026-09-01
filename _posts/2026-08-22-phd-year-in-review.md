---
layout: post
title: Reflections one year in
date: 2026-08-22 12:00:00
description: reflecting on a year of PhD work, gaussian splatting, and what I've learned
tags: phd research gaussian-splatting reflection
# categories: 
---

## Introduction
Some of the best advice I've heard is the saying: "if something is worth doing, it is worth doing poorly". Hence, this article! Stretching my writing muscle is definitely worth it and what better way to begin than reflecting on the first year of my PhD. 

I began my PhD in August '25 at the University of Virginia advised by Prof. Rohan Chandra, not entirely knowing what to expect from grad school. While I was coming into this with research experience from my undergrad and masters, a PhD felt instinctively different from the beginning. Some very common advice is that getting a doctorate is more marathon than sprint, but it didn't really hit me until a quiet moment after I had settled in, looked around and felt time passing much more slowly. Suddenly "five years" went from idle thoughts about what things would be like in 2030 to an immense chunk of time that seemed to barely me. But before I realized, two whole semesters went by paradoxically quickly. 

Here's me very clunkily transitioning to the list of one liners that I actually want to discuss.

### Picking a topic
I came into the PhD with general broad strokes ideas of what I wanted to do. For my masters thesis, I played around with the idea of how you could distinguish different instances of objects in the same general category. I imagined a robot trained to detect furniture
Whenever I looked at a demo of a robot being trained in a simulator, I used to be surprised at how visually unimpressive they looked. Surely a robot that is meant to operate on visual data from the real world real world shouldn't be trained on just the closest object you can find in a dataset or in an asset library? Why hope your policy generalizes if you can work with a digital copy of the actual object or scene you need to operate in as a 3D neural representation? My advisor pointed me towards the idea of sim2real systems and I was intrigued. I always thought Gaussian Splatting was an interesting idea: being able to generate photorealistic 3D objects explicitly composed of Gaussians that you can do whatever you want with seemed like the perfect fit for my interests.

And so, I began with the idea of using Gaussian Splatting as a way to capture simulated training environments for sim2real robotics. I began working immediately, and in my estimation at the time I got pretty far! I spun up a working pipeline that let me record a video on my phone, and have a trained splat and an invisible mesh (visible here) underneath it that let me render collisions as I see fit.

{% include figure.liquid loading="eager" path="assets/img/phd-year-in-review/splat_mesh_comparison.png" title="splat vs mesh comparison" class="img-fluid rounded z-depth-1" %}

I felt on top of the world, I no longer had to image what it would look like if a hundred untextured cubes quantum tunelled into my lab. 

{% include figure.liquid loading="eager" path="assets/img/phd-year-in-review/cube_collision_demo.gif" title="cube collision demo" class="img-fluid rounded z-depth-1" %}

I kept on iterating, letting my pipeline segment my scenes into objects with language inputs, collected a library of segmented out objects, each with its own bespoke mesh. No longer restricted to cubes, I accurately visualize throwing around our labs Jackals without getting a stern email from my advisor!

{% include figure.liquid loading="eager" path="assets/img/phd-year-in-review/jackal_splat_physics.gif" title="jackal physics splat demo" class="img-fluid rounded z-depth-1" %}

Until I started looking a little deeper for related work.

### First priniciples

I imagined using my pipeline to train navigation policies in cluttered environments and transfer them to the real world. It felt like a good idea and there seemed to be a gap in the literature: noone was using segmented out splats for navigation policies. Little did I know, there are some very impressive papers that did exactly this for manipulation. Slightly shaken, I began to see more holes in my initial assumptions, and realized I was implementing the wheel again. 

Chatting with some fellow grad students, it looked like this was a pretty common experience! If you have a spark of inspiration and an idea that excites you, derived from first principles, there is a staggeringly high chance that someone else has gone down that same line of reasoning. I want to stress that this isn't always true and that research isn't hopeless but that the entire field works off of the same knowledge base. In hindsight, I realize I should have switched things around. Spending a good chunk of time making sure that I was well oriented in the literature before excitedly plowing ahead would have saved me a lot of redundant work. 


Taking a broader view of the field got me over the Dunning-Kruger hump and has left me a more curious and well rounded researcher.
This next year, I'm going to make sure that I am careful about this. Orient, and then implement.

### The positives

Getting my hands dirty implementing the pipeline was helpful. There's nothing like running a method yourself to really understand where it fails. 

A year ago, I understood Gaussian splatting and sim2real but only in theory. For instance, I knew that splats are photometric methods and that they were not designed for accurate geometry, and that poorly constrained, noisy splats (affectionately called floaters) were really sticky to get rid of. But it isn't until I actually had to pick through a failed training run to realize that a trained splat that looks okay at eye level might be packed with camera-obscuring floaters close to the floor.

I can't tell you if I'll end up using this exact framework again, but I can confidently say that I understand the failure modes of each step of the pipeline. In the end my experience ended up paying off!
I spent a summer at Skydio using Gaussian splatting in a completely different setting (flying drones trying to map city blocks instead of grounded drones trying to navigate rooms) where knowing each failure mode and potential fixes helped immensely.

### Some mindset changes

There is no research without the researcher. Coming into the program I had a very simplified understanding of how I would do research: "Surely, if I have good ideas, run good experiments and write good code I'll be swimming in results!". I now realize that all of these things are preconditioned on how well you can manage your mindset. No small feat, I must say. There's a few things I noticed that I'm going to try and do differently.


Willpower and mental stamina are valuable commodities. My hypothesis is that saving on these resources is worth the cost of slightly suboptimal planning in the long run. "Marathon, not a sprint". I noticed myself spending time *deciding* to read a paper and spending energy wondering whether I spent my time correctly. I want to eliminate the time spent thinking about doing things in favour of actually doing them. This year, I want to try just doing things on a fixed routine and postponing analysis until way later.


I saw the same thing happening when I looked at things in hindsight. Past a certain point, there is no new information to be gained by reflecting on an experiment or project that didn't work out. Doing so takes up time and thus the mental resources I want to save. If we already knew what would work out as planned, there'd be no need to do any research!

### Moving forward

Getting a PhD is challenging endeavour filled with uncertainty, but I can say that I am thoroughly enjoying the process! 