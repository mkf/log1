---
title: "TIN05: having to do pixel-perfect html&css to match image, an exercise that felt really bad"
date: 2020-04-09T07:36:08+02:00
draft: false
---

Today i were doing a homework assignment task (https://kino.vm.wmi.amu.edu.pl/05en.htm#assessment-tasks) where we got an image and had to remake this:

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <title>Document Title</title>

    <!-- external CSS link -->
    <link rel="stylesheet" href="css/reset.css">
    <link rel="stylesheet" href="css/style.css">
  </head>
  <body>

    <div class="page">

      About

      Spirit has been working in the flower industry for 20 years. She began her work in San Francisco and has recently moved to Williamburg in Brooklyn, NY. She recently has transitioned to a lifestyle in which she enjoys frolicking in the fields on a daily basis

      Her specialty is flowers for hipster weddings. Please feel free to contact Spirit anytime if you are planning a wedding that involves teepees, quilts, or lace.


      LINKS
      http://en.wikipedia.org/wiki/Sunflower

    </div>

  </body>
</html>
```

```
    /*

    Style Hints:

    Body Font Size = 14px
    	 Font Family = "Times New Roman", serif
    	 Font Color = black
    	 Background: #F3EBE9

    H1 Font Size = 50px
       Font Family = Arial, Helvetica, sans-serif
       Text-transform: uppercase;
       color: #FFFFFF;	(White)

    H2: Font Size = 18px
    	Text-Transform: uppercase;
    	Font-Family: cursive, Helvetica, sans-serif;

    */
```

> # Hippie Portfolio
>
> Your client, Spirit Dunkin, has hired you to build the website for her flower shop. She has provided a mockup, in addition to all the images she wants to include. Your jobs is to update the HTML and CSS in the starter code to match her design as closely as possible.
>
> Two CSS helpers, `reset.css` and `normalize.css`, have been provided for your convenience. Feel free to use either, both, or neither. (You can read about each of them [here](http://meyerweb.com/eric/tools/css/reset/) and [here](https://github.com/necolas/normalize.css)). There are also a few hints in the `style.css` file to help get you started.
>
> Remember — small steps!

into this:

![orig.jpg](/to_posts/tin5-Apr9am-jpgs/orig.jpg)

Which would be then checked with

```sh
chromium-browser --headless --disable-gpu --screenshot --deterministic-fetch --window-size=1340,770 index.html
magick compare -metric AE -fuzz 15% orig.png screenshot.png diff-map.png
```

<pre>
•sturnix:~/DTIN-HTML-and-CSS-solution¶ ./grade.sh                                                          
Fontconfig warning: "/etc/fonts/fonts.conf", line 86: unknown element "blank"                              
[0409/013640.625718:ERROR:gpu_channel_manager.cc(397)] ContextResult::kFatalFail                           ure: Failed to create shared context for virtualization.                                                   
[0409/013641.097130:INFO:headless_shell.cc(619)] Written to file screenshot.png.                           
<strong>416715</strong>¬sturnix:~/DTIN-HTML-and-CSS-solution¶ ./grade.sh                                                    
Fontconfig warning: "/etc/fonts/fonts.conf", line 86: unknown element "blank"                              
[0409/020942.999819:ERROR:gpu_channel_manager.cc(397)] ContextResult::kFatalFail                           ure: Failed to create shared context for virtualization.                                                   
[0409/020943.940829:INFO:headless_shell.cc(619)] Written to file screenshot.png.                           
<strong>516915</strong>¬sturnix:~/DTIN-HTML-and-CSS-solution¶ ./grade.sh                                                    
Fontconfig warning: "/etc/fonts/fonts.conf", line 86: unknown element "blank"                              
[0409/021007.939440:ERROR:gpu_channel_manager.cc(397)] ContextResult::kFatalFail                           ure: Failed to create shared context for virtualization.                                                   
[0409/021008.907635:INFO:headless_shell.cc(619)] Written to file screenshot.png.                           
<strong>516926</strong>¬sturnix:~/DTIN-HTML-and-CSS-solution¶ ./grade.sh                                                    
Fontconfig warning: "/etc/fonts/fonts.conf", line 86: unknown element "blank"                              
[0409/021159.808248:ERROR:gpu_channel_manager.cc(397)] ContextResult::kFatalFail                           ure: Failed to create shared context for virtualization.                                                   
[0409/021200.693771:INFO:headless_shell.cc(619)] Written to file screenshot.png.                           
<strong>516915</strong>¬sturnix:~/DTIN-HTML-and-CSS-solution¶ ./grade.sh                                                    
Fontconfig warning: "/etc/fonts/fonts.conf", line 86: unknown element "blank"                              
[0409/025418.122823:ERROR:gpu_channel_manager.cc(397)] ContextResult::kFatalFail                           ure: Failed to create shared context for virtualization.                                                   
[0409/025419.639026:INFO:headless_shell.cc(619)] Written to file screenshot.png.                           
<strong>50090</strong>
</pre>

My result so far, with some really nasty CSS and general practices, but generally done lazily, although with heavy use of GIMP for analysis:

![screenshot.jpg](/to_posts/tin5-Apr9am-jpgs/screenshot.jpg)

![diff-map.jpg](/to_posts/tin5-Apr9am-jpgs/diff-map.jpg)

It felt like a very bad waste of time and a worthless experience.

The task supposedly evolved from

> Template webpage for 5th class of Internet Technologies course.
>
> Initial version by Felipe Gonzalez (GitHub: pipe2705)
https://github.com/pipe2705/html-css-homework
