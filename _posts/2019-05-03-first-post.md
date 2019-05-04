---
layout: post
title: TUCTF_Literal
subtitle: TUCTF{R34L.0N35.4R3.D4NG3R0U5}
tags: misc easy 
---

## Literal [MISC 50]

## DESCRIPTION:
Something's going over my head,and it's too fast for me to catch!

## CHALLENGE:
http://18.222.124.7

![Literal](literal.png)

## DIFFICULTY:
EASY! 

Well This Challenge was a cakewalk. The link was redirecting to another webpage on Wikipedia. To Solve this We just stopped the loading of webpage and viewed the source of page (CTRL+U) http://18.222.124.7/Literal.html. It gave something like this:

```HTML

<html>
  <head>
  <meta http-equiv="Refresh" content="1; url=https://en.wikipedia.org/wiki/Fork_bomb">
  </head>
  <body>
  <!--
        *   *                     f   f   f
      *  ** *                   ff  ff  ff
      * * ** ||                ff  ff  ff
    **   ||||T||              fUffffffff
      *   |C|||T| oooooooooooo fFff
           |||||||{ooooooooooRfff3o
          ooo4ooooooooooooooLff.ooooo0
        oooNooooooooooooooo3ooooooo5ooo.
        oooo4oooooRoooooooooo3oooooooooo.
        oooDooooo4oooooNooooooooooooooooo
        ooooooooooooooGoooooooooooooooooo
        ooooooooooooooooooooo3oooooooooRo
         oooooooo0oooooooooooooooooooooo
          oooooooffUoooooooooooooooooo
            ooofff5ooooooooooooooooo
             fff }ooooooooooooooo
            fff
  -->
  Redirecting to Wikipedia...!
  </body>
</html>
```

Looking closely to BOMB and extracting the TUCTF{} the capital Letters and digits....
### FLAG:
### TUCTF{R34L.0N35.4R3.D4NG3R0U5}
