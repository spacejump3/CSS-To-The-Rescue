# CSS-To-The-Rescue
I will be making a an atomic explosion...

## Week 1
In the first week we were able to choose our theme's. I had many idea's for 3 of the themes, but then I came up with the idea of creating a nuclear explosion in CSS with the fireworks theme. After I got approval of Sanne to do it, I started thinking about what I am gonna create.

### First thoughts
So obviously I need SOME sort of particle emmitter style setup to create this. I can't literally make a particle emitter which is randomized, but I should be able to make something that LOOKS randomized. Since you can infinitely loop animations in CSS, I can contiously 'spawn' elements. So I definitely have to think about that. I also want the user to be able to slightly customize the explosion by being able to choose to add a shockwave, radiation cloud and initial flash. I specifically want the user to be able to turn that off or on because if anyone with epilepsy stumbles across this project, I don't think they'd appreciate the bright lights... 

I initially wanted to add a sound for when the shockwave reaches you, but I'm not sure if it's possible? But as I'm writing this I thought of an idea: is it possible to create an audio tag which when you press the button starts the audio. The audio however is around 30 seconds of silence but at the end has a shockwave sound. In my head this sorta makes sense but I'd have to test this out. In any case, you are also able to select the distance and depending on where you are, the shockwave will reach you faster or slower. If I have extra time I might want to add a close-up slowmotion option which would show the <a href="https://www.youtube.com/watch?v=A9S3MUxH680">rope trick effect</a>. Honestly I think it looks insane and would love to recreate this in CSS, but I think this could even be a project of it's own so for now it's in the backburner...

I also want to add atomic goggles which you HAVE to wear because it will render you blind otherwise. As a safety, if you have flashing lights turned off, you won't be able to press the button at all. If you have flashing lights turn on you will be able to press the button to which you will only see a bright flash. Now that I'm typing this I am doubting how I am supposed to do this system without JavaScript, but I'll have to think about that or think of something else.

### Features and sketch
The features I want to add are:
- Light / Dark mode (daytime or nighttime)
- Shockwave / radiation cloud / initial flash toggle
- Distance selector
- Atomic goggles
- Choose color of nuke? Maybe a fun option to add

![Nuke schets-01](https://github.com/spacejump3/CSS-To-The-Rescue/assets/112871518/aa469821-f5ac-4662-95e9-2b91e3b3361b)

Above is my first sketch I made and I tried to explain which part should be what element. I might have to change the button for an audio tag instead. Or atleast let the audio tag play somehow if it's checked? I need to know if this is possible!

## Week 2

### Struggling
So I started initially by making the control panel. I just used a form and some fieldset to create a rough control panel where I can detonate my bomb. Then, I created a very simple animation of the initial blast. It was basically a simple animation of a circle expanding very quickly. I used a radial gradient to create a motion blur effect and it looked pretty nice. Using ```:has()``` I was able to link the detonate button with the explosion so that the button triggers the blast. 

So that's where it ended for day one.. And day 2 mostly. In day 2 I really wanted to start with the actual mushroom cloud but I couldn't get started. I had already attended the randomness workshop but I didn't feel like I could add it to my project. I tried to make a simple animation of a single fireball increasing in size and then decreasing while going down, but I just couldn't make it smooth. In After Effects I can do this in 3 seconds with a blindfold, but in CSS I was just struggling. I couldn't work out how to actually make it smooth in CSS since keyframes work just slightly different in CSS, but it's significant enough that I couldn't make it work. When I tried to change the size while the position was going down somehow It cancelled out the position keyframes which just made me MAD. I had to add every keyframe individually, but then the keyframes would add easing to each keyframe. I tried making it smooth using ```cubic-bezier``` but that was just more frustration. It's nearly impossible to smoothly transition between keyframes using ```cubic-bezier```. I was extremely frustrated so I went home early since I couldn't get anything done.

When I got home, I finally made progress...

### I am become death...
So when I got home, after a small break I looked up HOW to keyframe two properties (position and scale) and make it make smooth. Turns out, just use two animations...... Literally make one animation move it down, and use the other to scale it. That's it. Well now that I had a smooth animation, I could add more smoke and fire! I just made a bunch of div's and then individually changed the width/height and position. This made it look very random. I used the same technique for the 'shaft'. At this point the nuke started forming:

![nuke](https://github.com/spacejump3/CSS-To-The-Rescue/assets/112871518/4de6c556-22ec-4b28-b57d-127cd7f009ac)

It's still a bit messy and the way I randomized the blobs is not very good, so there's still some cleaning up but it's definitely taking shape! Here is the code by the way:

```css
/* general blobs */
article:nth-of-type(2) div {
    position: absolute;
    scale: 0;

    animation: down 3s ease-in-out infinite, scale 3s ease-in-out infinite;
}

/* blobs 1-5 */
article:nth-of-type(2) div:nth-of-type(1) {
    width: 5em;
    height: 5em;
    left: 10%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;
}

article:nth-of-type(2) div:nth-of-type(2) {
    width: 8em;
    height: 8em;
    left: 20%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 1.9s;
}

article:nth-of-type(2) div:nth-child(3) {
    width: 12em;
    height: 12em;
    left: 20%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 1.4s;
}

article:nth-of-type(2) div:nth-child(4) {
    width: 10em;
    height: 10em;
    left: 50%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 0.3s;
}

article:nth-of-type(2) div:nth-child(5) {
    width: 9em;
    height: 9em;
    left: 25%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 0.5s;
}

/* blobs 6-10 */
article:nth-of-type(2) div:nth-child(6) {
    width: 7em;
    height: 7em;
    left: 40%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 1.3s;
}

article:nth-of-type(2) div:nth-child(7) {
    width: 5em;
    height: 5em;
    left: 60%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: 1s;
}

article:nth-of-type(2) div:nth-child(8) {
    width: 6em;
    height: 6em;
    left: 30%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: -.5s;
}

article:nth-of-type(2) div:nth-child(9) {
    width: 8em;
    height: 8em;
    left: 10%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: -.2s;
    /* outline: solid 1em; */
}

article:nth-of-type(2) div:nth-child(10) {
    width: 6em;
    height: 6em;
    left: 60%;

    border-radius: 67% 34% 25% 74% / 60% 82% 31% 54%;

    animation-delay: -.7s;
}
```

...So yeah, literally individually changing each div. I will change this and make this MUCH cleaner using probably the randomization technique which I learned from Nils Binder.



IK HEB DEZE GEVONDEN ECHT HANDIG DENK IK!!!! https://csscrafter.com/css-particle-effects/
